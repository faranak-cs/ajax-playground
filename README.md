# Ajax Playground
Interact with server, simply using XHR() object without using any third-party library.

## Getting Started
There are four ways to trigger a HTTP request in the context of HTML:
- Links:
```
<a href="http://localhost:8080/getProducts">Get Products</a> 
```
- Forms:
```
<form action="/get_products.php" method="get">
```

- Cookies:
```
<?php

setcookie("user", "Faran");
echo $_COOKIE['user'];

?>
```

- JavaScript (Ajax):
Making an Ajax call from JavaScript means sending an asynchronous request to a server to fetch or send data without reloading the web page. OR use a HTTP Client such as Axios.

## Key Concepts
- XMLHttpRequest object
- Promises
- Fetch API
- Streams API
- Async/Await

Callbacks -> Promises -> Async/Await
  
### XHR
#### Constructor Function
```
function Person() {
  return new.target;
}

// Return the function definition
let person = new Person();

// Return nothing
let person = Person();
```

#### Ajax Call
The following are the steps to perform an ajax call:
```
// Create an object using XHR constructor function
let xhr = new XMLHttpRequest();

// Configure the connection
xhr.open("GET", "http://localhost:8080/getProducts");

// Configure the callback function
xhr.onload = () => {
document.getElementById('products').innerHTML = this.responseText;
}

// Send request to the server
xhr.send();
```
#### Properties
- readyState
```
if (xhr.readyState === 4 && xhr.status === 200){
  // logic
}
```

### Promises
Introduced in ES6. Series of nested function calls.
- resolve()
- reject()

### Fetch API
Fetch uses Promises. Runs separately on network thread. 
```
fetch(url)
  .then(data)
  .then(data)
  ...
  .catch(error)
```
- json() : returns a promise
```
let url = "http://localhost/8080/products"
let myHeaders = {
  "Accept" : "application/json"
}
fetch (url, {
  headers : myHeaders
})
  .then (res => {
    return res.json();
})
  .then (data => {
    condole.log(data)
})
```

### Streams API
- Response.body : returns ReadableStream object
- ReadableStream.getReader() : returns a reader
- READER.read() : reads a stream

### Async/Await
JavaScript is synchronous, single-threaded (main thread) language. In order to communicate asynchronously with the server, the processing has to be done somewhere else. In this way, the main thread will be free to use.
- Fetch with async/await

## Useful Links
- https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest
- [What the heck is the event loop anyway? | Philip Roberts | JSConf EU](https://youtu.be/8aGhZQkoFbQ?si=iZkOZ_vSr5RFWqWe)
- https://developer.mozilla.org/en-US/docs/Web/API/Streams_API
