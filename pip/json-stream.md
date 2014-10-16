This is used inside crosscloud.js; it's suitable for use with
window.postMessage or socket.io.

Communication occurs by exchange of JS objects.  Assume only JS
objects which can be faithfully serialized as JSON, although it might
not actually get serialized.  See [cloning][https://developer.mozilla.org/en-US/docs/Web/Guide/API/DOM/The_structured_clone_algorithm].

client says:

{op:"begin-query",

}

server says

...

