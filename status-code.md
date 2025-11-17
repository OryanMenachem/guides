# Common HTTP Status Codes

## 1xx – Informational

- **100 Continue** – The server received the request headers, the client should continue sending the body.
- **101 Switching Protocols** – The server is switching protocols as requested by the client.

## 2xx – Success

- **200 OK** – The request was successful, and the server returned the requested data.
- **201 Created** – The request was successful, and a new resource was created.
- **202 Accepted** – The request is accepted but not yet processed.
- **204 No Content** – The request was successful, but there is no content to return.

## 3xx – Redirection

- **301 Moved Permanently** – The requested resource has moved to a new URL permanently.
- **302 Found** – The requested resource is temporarily at a different URL.
- **304 Not Modified** – The resource has not changed since the last request (used for caching).

## 4xx – Client Errors

- **400 Bad Request** – The server could not understand the request due to invalid syntax.
- **401 Unauthorized** – Authentication is needed to access the resource.
- **403 Forbidden** – The client does not have permission to access the resource.
- **404 Not Found** – The requested resource does not exist.
- **405 Method Not Allowed** – The request method is not allowed for the resource.
- **409 Conflict** – There is a conflict with the current state of the resource.
- **422 Unprocessable Entity** – The request was well-formed but cannot be processed (often validation errors).

## 5xx – Server Errors

- **500 Internal Server Error** – The server encountered an unexpected error.
- **501 Not Implemented** – The server does not support the functionality required.
- **502 Bad Gateway** – The server received an invalid response from the upstream server.
- **503 Service Unavailable** – The server is currently unavailable (overloaded or down for maintenance).
- **504 Gateway Timeout** – The server did not get a response in time from the upstream server.
