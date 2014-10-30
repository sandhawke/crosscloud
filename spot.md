Simple Page-Owner Token (SPOT) Authentication
---------------------------------------------

This document specifies an HTTP authentication mechanism suitable for use in situations where the HTTP client is tightly coupled with another HTTP server.  It is very easy to implement and requires no extra crypto.

For illustration purposes, we'll say Alice is a process which serves the web resource at http://alice.example/alice and wants to act as a client to access a protected resource http://bob.example/bob, which is served by a different process, Bob.

For non-trivial use, to provide some resistance against attackers who can view or intercept network traffic or subvert the DNS, HTTPS URIs should be used and clients should check that the server DNS name matches the certificate.

Walkthrough
===========

**Step 1.**  Alice performs an HTTP GET on an access-controlled page served by Bob, but does not authenticate herself, so Bob returns a 401 error.  The response includes a header telling Alice she can authenticate using this protocol and try again.

```http
> GET /bob HTTP/1.1
> Host: bob.example

< HTTP/1.1 401 Authorization Required
< WWW-Authenticate: Page-Owner-Token
```

This uses the standard WWW-Authenticate HTTP header with a new keyword
for this new authentication type.

**Step 2.**  Alice generates a cryptographicly random token, a nonce. In 
this example, I'll write it as xyz123.   It should use only the Base64 characters.

**Step 3.**  Alice repeats the GET, this time including a header which identifies her via a web page and includes the nonce:

```http
> GET /bob HTTP/1.1
> Host: bob.example
> Authorization: Page-Owner-Token client="http://alice.example/alice" token="xyz123"
```

ISSUE: Should it just be http://alice.example/ ?   What does it mean to include the /alice?

Alice can include multiple headers like this, since it might be that only one of her multiple identies actually has access to /bob and she doesn't now which.  The identity strings must be dereferenceable.  They can be either an Information resource IRI (returning 200 OK) or a non-information resource IRI (returning 303, or having a hash).   Either works fine for this protocol.

Note that sending identity strings like this may reveal more to Bob than desirable.

**Step 4.**  Bob checks to see if the request provides a valid token:

```http
 > HEAD /alice HTTP/1.1
 > Host: alice.example
 > Page-Owner-Token-Check: token="xyz123" relying-party="http://bob.example/bob"
```

The verb could be GET (instead of HEAD) if the Bob is interested in
the content of /alice.

**Step 5.**  Alice confirms:

```http
< HTTP/1.1 200 OK
< Page-Owner-Token-OK: true
< Set-Cookie: [whatever, optional]
```

Alice only does this if the token was in fact the one she generated for her GET to Bob.

Only a response containing the header "Page-Owner-Token-OK: true" is taken as confirmation.

The Set-Cookie is an optional shortcut.  With this cookie, Alice can give Bob some secret to use in future communications, so that Bob can act as an HTTP client accessing alice.example in the future without needing to go through his own SPOT handshake.

**Step 6.**  Bob returns the protected content requested in Step 3

```http
< HTTP/1.1 200 OK
< Set-Cookie: [whatever, optional]
... content ...
```

The Set-Cookie is an optional shortcut.  With this cookie, Bob can give Alice some secret to use in future communications, so that Alice and Bob do not have to repeat this handshake every time.

Status
======

Not yet implemented.

Before wide deployment, the new authentication type Page-Owner-Token and the two new HTTP headers (Page-Owner-Token-Check and Page-Owner-Token-OK) should be registered with the IETF.