---
title: What is HTTP?
date: "2020-05-15T12:40:32.169Z"
description: What is HTTP and how does it work?
---

# What is it?

- **H**yper **T**ext **T**ransfer **P**rotocol
- Communication between web servers & clients
- Stateless
  - Every request is independent. whether you visit. reload, it doesn't remember anything about previous session.
  - You can utilize local storage, cookies, sessions etc. but HTTP at its core is stateless.
- HTTPS
  - Hyper Text Transfer Protocol Secure
  - Data encrypted

### HTTP METHODS

1.  **GET**

- Retrieves data from the server.
- Loading a page, assets, json data, xml data and so on.
- Every time you visit a page, you're making GET request to the server

2.  **POST**

- When you are posting data to the server, adding something to the server.
- When you submit a form, blog post

3.  **PUT**

- Update data already on the server
- Think blog post you want to edit.

4.  **DELETE**

- Deletes data from the server

### HEADER & BODY

With each HTTP request and response, you have something called a header and a body.

1.  **BODY**

- The body with a response is the data that's going to load on the page, whatever is being sent from the server.
- When you make a request, you can also send a request body.
  - When you submit a form, the form fields you are submitting is a part of the request body.

2.  **HEADER**

```
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Type: application/json
Content-Length: 257
Host: google.com
User-Agent: HTTPie/0.9.3
```

- General header
  - Request URL: URL you're requesting
  - Request Method: if it's a GET request, POST request and so on
  - Status code: Covered deeper
  - Remote address: IP of the remote computer
  - Referrer Policy: if you go to a page from another page, it might have some information
- Response header
  - Server: if its apache, ngnix or something like that. A lot of times, it's hidden just to prevent hackers from knowing what type of server the website uses.
  - Set-Cookie: cookies from the server to the client.
  - Content-Type: text/HTML, text/CSS, image/png, application/JSON, and so on.
  - Content-Length
  - Date
- Request header
  - Cookies: If you have a cookie that was previously sent by the server and you need to send it back to the server, you'd do it in this field
  - Accept-xxx: accept encoding, character set, language, etc
  - Content-Type
  - Content-Length
  - Authorization: some kind of token, so that you can validate a user to access a protected router or protected page
  - User-Agent: long string that has something to do with the software the user is using
  - Referrer: info regarding the referring site

### HTTP STATUS CODES

**1xx: Informational**

Request received /processing

**2xx Success**

Successfully Received, understood and accepted

- 200 - OK
- 201 - OK created

**3xx Redirect**

Further action must be taken / redirect

- 301 - Moved to new URL
- 304 - Not modified (Cached version)

**4xx Client Error**

Request does not have what it needs

- 400 - Bad request
- 401 - Unauthorized
- 404 - Not found

**5xx Server Error**

Server failed to fulfill an apparent valid request

- 500 - Internal server error
