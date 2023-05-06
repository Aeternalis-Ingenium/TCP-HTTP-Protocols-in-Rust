# HTTP Server

---

This directory consists of the implementation for the 3 components of an HTTP server:

* Server
* Router
* Handler

The URLs will be available at:

* `localhost:3000/`
* `localhost:3000/health`
* `localhost:3000/api/shipping/orders`
* `localhost:3000/invalid-path`

## Server

The server module contains the struct `Server` that accepts a new socket address (host & port) while listening to incoming connection.

### Method

* The `new()` method initializes the Server instance with the socket address.

* The `run()` method performs the following:
  * Socket binding.
  * Listening to incoming connections.
  * Byte stream reading from a valid connection.
  * Converting the stream to an `HttpRequest` struct instance.
  * Passing the request to `Router` struct for further processing.

## Router

The router module is responsible to inspect incoming HTTP requests and to route the request to the correct handler for further processing.

### Method

* The `route()` is the method that determines the correct handler for the incoming request by doing the following:
  * If the `GET` request route begins with `/api`, it routes the request to the `WebServiceHandle`.
  * If the`GET` request is for any other resource, it assumes the request is for a static page and routes the request to the`StaticPageHandler`.
  * If it is not a`GET` request, it sends back a **404** error page.

## Handler

The handler module is where we implement the trait that process the incoming connection accrodingly. This module also has 4 data structures:

* `StaticPageHandler`
* `WebServiceHandler`
* `PageNotFoundHandler`
* `PrderStatus`

### Method

The trait `Handler` owns 2 methods:

* The `handle()` is a method that handles any other user data type for the trait implementation.
* The `load_file()` is a method to load a non-`json` file from public directory into the httpserver root directory.

### Processing

* `StaticPageHandler`:
  * If incoming request is for localhost:3000/, the contents from file index.html is loaded and a new HttpResponse struct is constructed
  * If incoming request is for localhost:3000/health, the contents from file health.html is loaded, and a new HttpResponse struct is constructed
  * If the incoming request is for any other file, the method tries to locate and load that file in the httpserver/public folder. If a file is not found, it sends back a 404 error page.
  * If the file is found, the contents are loaded and embedded within an HttpResponse struct. Note that the Content-Type header in HTTP Response message is set according to the type of file.

* `WebServerHandler`:
  * If the GET request is for localhost:3000/api/shipping/orders, the json file with orders is loaded, and this is serialized into json, which is returned as part of the body of the response.
  * If it is any other route, a 404 error page is returned.

---
