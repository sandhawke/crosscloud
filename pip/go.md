This is the interface to a 'datapages' view of part of the Web.  It
can be used inside a web server, as this interface is provided by
PageStore or inside a client, as this interface is also provided by
PageClient.

It is a thread-safe interface.  All of the calls can be considered
atomic.  Concurrency is handled Web-style, with ETags.  Many of these
calls block while waiting for network access, if you're using
PageClient.  Some of them can block forever, as they are waiting on
real-world events like data changing.

We have a very interesting view of Web pages.  Essentially we view
each page as a JSON object.  Looking slightly closer, we view them a
grow+json object or, equivalently, as an RDF Dataset whose default
graph contains triples whole only non-blank subject is the URL of the
page.  That is, each page is set of properties and their values.

When the Web Page doesn't natually adhere to this form, we wrap it so
it does.  For example, an HTML page would look something like:

```json
{ "content": "<html><head>....</head><body> ...</body></html",
  "contentType": "text/html",
  ... available page metadata ....
}
```

In this view, metadata (which might actually be stored in a
different resource available via rel=describedby) is readily available
in the JSON object.


CRUD Operations
===============

The CRUD operations (Create, Read, Update, Delete) are available on a
PageClient or directly on a local PageStore.

```go

type PageData map[string] interface{} // or and RDF Dataset?

type PageState struct {
  Id string
  ETag string
  LastModified time.Time
  Data PageData
}


client.Create(prefix, slug string, copyFrom *PageData) PageState, Err
```

Constructs a new page with a new unique `Id`, which is prefix+slug,
but might alter slug to make the resulting `Id` be unique.  Pass
`slug` as "" for no preference.  Fails if this user can't write to the
space beginning with prefix.

If `copyFrom` is non-nil, that becomes the initial state; otherwise an
empty resource is created.

Deleted page Ids are not immediately reassigned by `Create``, but might
be after a long period (hopefully many months, if the server can
remember that long).

```go
client.Read(page *PageState, waitForChanges time.Duration) Err
```
 
Reads the page `page.Id` and updates the values to its current state.  Also updates ETag and LastModified to match most recent state change.  Id might also have been changed via a Rename/Forward operation.

If `waitForChange`>0 then do not return until the etag is different from `page.ETag` (that is, the page has changed), or that duration has been exceeded.  If the waitForChange timeout is exceeded, then the operation returns as soon as the state has been obtained, even if it has not changed.   (This is distinct from a network timeout.)

Special values of page.ETag may be set: client.Absent (blocks until the page exists), and client.Empty (blocks until the page is not empty), client.AbsentOrEmpty (blocks until page is present and non-empty).

Fails if id page does not exist, or this client's user does not have read permission.


```go
client.Replace(fullPage *PageState) Err
client.Overlay(partialPage *PageState) Err
```

Modify the state of page with id `.Id`.   

If the parameter page has an ETag other than client.Any, it must match the current state or the update is aborted, signalling someone else unexpectedly modified the page.

After the operation, ETag and LastModified are updated.

`Replace` sets the entire state of the target page; `Overlay` only sets those which are present in `partialPage` (using `nil` as a signal that a property is to be removed).


```go
client.Delete(page *PageState) err(eperm, wrongETag)
```

Causes the page to be deleted, looking only at `page.Id` and `page.ETag`.  Like the update operations, it aborts if the remote page's ETag does not match.

```go
client.DeletePrefix(prefix string) Err
```

Causes all pages whose Ids start with `prefix` to be deleted.

```go
client.RenamePrefix(oldPrefix, newPrefix string) err
```

Requests the server to move any/all current pages (and possible new pages) with Ids starting with oldPrefix to start with newPrefix.   Other systems may be notified of the move when it happens, and requests to the old area will be forwarded for some time.

It is an error if any of the oldPrefix space is already forwarded.



Client Operations
=================

```go
client.Login(...)

client.SetVocab(...)   // allows mapping between RDF and JSON

client.SetNetworkTimeout(t time.Duration)
```

TBD


Querying
========

```go

type Cursor interface {
	func Restart()   // call to reset cursor to beginning
    func Next() page *PageState, resultsModified bool
    func EstimatedRemaining() uint
    func Error() Err
    func ContinuationFilter()  // constructs a filter that would start here
    func QueryETag()  // the ETag of the query response
	func Stop()
}

type Filter map[string] interface {} // subset of mongoDB

client.Query(filter Filter, onlyProperties, sort []string, limit uint) Cursor

client.Dump(waitForNotETag) Cursor
```

`Dump` returns an iterator on all available pages.  For PageStore, it's all stored pages.  For PageClient, it's all cached pages.

`Query` returns an iterator over all available pages which match the filter, which is a MongoDB-like QBE filter expression.  

If `onlyProperties` contains any strings, only those properties are shown; the resulting page images are subset views of the actual pages.

If `sort` contains any strings, they each name a property, or "-" followed by the name of a property, and that forms the sort order.   Without the minus, sort is ascending (like 1,2,3); with the minus sort is descending (like 3,2,1).

`limit` sets the maximum number of results returned.   There is no value for unlimited; one should always consider the maximum that might reasonably be handled.

`Cursor.ContinuationFilter()` constructs a modified version of the filter such that using it in a query would return the query results after this result.  One could, in theory, call iter.Next() once to get the first result, then use ContinuationFilter() to construct a new query, call its iter.Next once to get what would have been the second result of the original query, etc.   This is useful if a query needs to be paused and possibly never resumed, such as with a RESTful paging interface. 

`Cursor.Next()` returns the next result of the query (or the first if this is the first time Next() is called for this query) and also a boolean flag to indicate whether the query result set has changed since the first result was returned for this cursor.    If a consistent query result set is needed, one must Restart whenever this happens, like this:

Typical structure:

```go
q := client.Query(...)
for (page, modified := q.Next(); page != nil; ) {

    if q.Error() { ... handle error ... }

    // consider doing this:
    if modified { q.Restart();  continue }

	// do something with 'page'

```

The pointer to a PageState returned by Next() is to an ''internal'' structure in the Cursor. What happens to that structure when you call q.Next() is undefined.

You ''may'' modify that PageState and call client.Overlay or client.Replace to push the modification back to the server.   It is an error to call client.Replace if you set onlyProperties, since that would erase any unexpected properties.

See http://stackoverflow.com/questions/14000534/what-is-most-idiomatic-way-to-create-an-iterator-in-go

