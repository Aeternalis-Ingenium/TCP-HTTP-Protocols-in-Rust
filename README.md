# Protocols for Internet Communication

How do apps (web, mobile) communicate with each other in the internet?

* The TCP/IP model is a simplified set of standards and protocols for communication over the internet. This model is organized into 4 layers:
  * Network Access Layer
  * Internet Layer
  * Transport LAyer
  * Application Layer
* TCP is the transport-layer protocol over which other application-level protocols such as HTTP operate.
* HTTP is an application layer protocol and is the foundation for most web services. HTTP uses TCP in most cases as the transport protocol.

## Project

This repository consists of 4 mini projects to learn about the foundation of TCP/IP and HTTP protocols:

* `tcpserver/`:
  * Utilization of `TcpListener` to listen to the incoming connection requests.
* `tcpclient/`:
  * Utilization of `TcpStream` to connect to `localhost:3000`.
* `httpserver/`:
  * **Server** $\rightarrow$ Listening for incoming TCP byte streams.
  * **Router** $\rightarrow$ Accepting HTTP requests and determining which handler to invoke.
  * **Handler** $\rightarrow$ Processing the HTTP requests and constructing HTTPS responses.
* `http/`:
  * **HTTP Library** $\rightarrow$ Interpreting the byte stream and converting it to HTTP request.

### Summary

These are the implemented components in the `protocols` directory:

* The TCP/IP model is a simplified set of standards and protocols for communication over the internet. It is organized into four abstract layers: Network Access layer, Internet Layer, Transport Layer and the Application layer. TCP is the transport-layer protocol over which other application-level protocols such as HTTP operate. We built a server and client that exchanged data using the TCP protocol.
* TCP is also a stream-oriented protocol where data is exchanged as a continuous stream of bytes.
* We built a basic TCP server and client using the Rust standard library. TCP does not understand the semantics of messages such as HTTP. Our TCP client and server simply exchanged a stream of bytes without any understanding of the semantics of data transmitted.
* HTTP is an application layer protocol and is the foundation for most web services. HTTP uses TCP in most cases as the transport protocol.
* We built an HTTP library to parse incoming HTTP requests and construct HTTP responses. The HTTP requests and responses were modeled using Rust structs and enums.
* We built an HTTP server that serves two types of content - static web pages (with associated files such as stylesheets), and json data.
* Our web server can accept requests and send responses to standard HTTP clients such as browsers and curl tool.
* We added additional behaviour to our custom structs by implementing several traits. Some of them were auto-derived using Rust annotations, and others were hand-coded. We also made use of lifetime annotations to specify lifetimes of references within structs.

---

## Reference

I learn the implementation of TCP and HTTP protocols in Rust mostly from this amazing book (click on the link to buy one):

> Eshwarla, P. (2023). [Rust Servers, Services, and Apps (Early Access)](https://www.manning.com/books/rust-servers-services-and-apps). Manning.

**Disclaimer: I'm not in any way paid to suggest the above book. It is just an amazing book!**

--
