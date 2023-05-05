# Distributed Web Application with Rust

## Web Server

The web server will contain 4 components:

* **Server** $\rightarrow$ Listening for incoming TCP byte streams.
* **Router** $\rightarrow$ Accepting HTTP requests and determining which handler to invoke.
* **Handler** $\rightarrow$ Processing the HTTP requests and constructing HTTPS responses.
* **HTTP Library** $\rightarrow$ Interpreting the byte stream and converting it to HTTP request.

---
