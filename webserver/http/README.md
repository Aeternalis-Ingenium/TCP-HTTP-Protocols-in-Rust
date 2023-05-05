# HTTP Library

HTTP stands for Hyper-Text Transfer Protocol. It is the standard communication method in the internet.

---

## HttpReqeust

Since Rust doesn't provide an http library, we construct a struct called `HttpRequest` with the following core logic:

* Read each line in the incoming HTTP request. Each line is delimited by CRLF (\r\n).
* Evaluate each line as follows:
  * If the line is a request line (we are looking for the keyword HTTP to check if it is a
request line as all request lines contain HTTP keyword and version number), extract the
method, path and HTTP version from the line.
  * If the line is a header line (identified by separator ':'), extract key and value for the header item and add them to the list of headers for request. Note there can be multiple header lines in an HTTP request. To keep things simple, let’s make the assumption that the key and value must be composed of printable ASCII characters (i.e., characters that have values between 33 and 126 in base 10, except colon).
  * If a line is empty (\n\r), then treat it as a separator line. No action is needed in this case.
  * If the message body is present, then scan and store it as `String`.
