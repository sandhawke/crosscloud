This is the interface to a datapages pagestore, which might be many
pods for many users, as well as pages which are not local.

CRUD Operations
===============

The CRUD operations are available on a PageClient or directly on a
local PageStore.

`go
type Meta struct {
  id string
  etag string
  lastmod time.Time
}

type State map[string] interface{};    // JSON obj; or maybe RDF Graph...?

client.Create(prefix, slug string, newData State) Meta, Err
`

Constructs a new unique id as prefix+slug, but might alter slug to
make the resulting id be unique.  Fails if this user can't write to
the space beginning with prefix.

Then saves newData to that location.  newData may be nil, in which
case an empty resouce is created.  Deleted pages are not immediately
reassigned by Create, but might be after a long period (hopefully
months, at least).

`go
client.Read(id, waitNotETag string) State, Meta, Err
`
 
Returns the latest version of the data and the corresponding metadata.
The meta.id might be different from id if it has changed and been
forwarded.

This this call will block until the given page no longer has the given
etag.  Special etag values client.Any (just return immediately),
client.Absent (blocks until the page exists), and client.Empty (blocks
until the page is not empty), client.AbsentOrEmpty (blocks until page
is present and non-empty).

Fails if id page does not exist, or this client's user does not have
read permission.


`go
client.Replace(id string, newData State, currentETag string) Meta, Err
client.Overlay(id string, changes State, currentETag string) Meta, Err
`

Modify the state of page id according to the State parameter, of currentETag is still the etag.

Replace sets the state to `newData`, while `Overlay` only changes the parts of the state that are present in `changes`.   A null value causes that part of the state to be removed.

client.Any may be given as an ETag if the operation is to be carried out regargless of the current ETag.


`go
client.Delete(id, currentETag string) err(eperm, wrongETag)
`

Causes the page to be deleted, if it still has etag currentETag.


Client Operations
=================

`go
client.Login(...)

client.SetVocab(...)
`

TBD


Querying
========

`go

type PageIterator interface {
    func Next() State, Meta, Err
}

client.Query(filter, waitNotETag, onlyProperties, sort, limit) PageIterator

client.Dump(waitNotETag)
`

See http://stackoverflow.com/questions/14000534/what-is-most-idiomatic-way-to-create-an-iterator-in-go

client.modificationCount()

client	.lastModification() id, etag, lastmod
    which you can check to see if anything changed during iter.
