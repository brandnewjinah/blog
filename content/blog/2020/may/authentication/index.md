---
title: How does authentication work?"
date: "2020-05-25T12:40:32.169Z"
description: Authentication breakdown
---

# How does basic HTTP authentication work?

note taken from medium article by [Jignesh Kakadiya](https://medium.com/@bitshadow/how-basic-http-authentication-and-session-works-d29af9caec31)

**Client Side:**

- You type url and press enter
- Client finds the server to talk with, DNS resolutions, 2 way handshake etc.
- Client sends a request to the server for getting the data corresponding to the path "/"

**Server Side:**

- Server gets the request and goes to pull the content for the request
- Server sends response back to the client containing the document browsers can render on the screen.

### 2. Signup

**Client Side:**

- Fill out user id and pw
- browser sends a request containing your id and pw to the server.

```
The HTTP request looks like this:
---------------------------------
request: POST / HTTP/1.1
         Host: medium.com
         Content-Type: application/x-www-form-urlencoded
         Content-Length: 30

         userid=foo&password=mypassword
```

**Server side:**

- Receives the request, extracts the data (credentials) and creates an entry in their database with userid and password
- if created successfully without any conflict, Server redirects user to login page.
  - otherwise, throws some error message
- to protect your pw, server creates hash of password and stores it

```
password_hash = hash.create('mypassword', ‘sha-1’);
// password_hash = 2ef5aa5a037ae1be9c7cdd15649cf9fc686ddee2
// used sha-1 (Secure Hash Algorithm 1) for generating hashed password
```

### 3. Login

**Client Side:**

- Browser sends credentials (id, pw) via login form, which points to for ex: "/login"

**Server Side:**

- Server gets request, extracts userid and pw
- Searches for that userid in the database, extracts pw for that userid, and compares pw against pw sent by the client.
- if hashed pw stored, it checks hash value.
- if pw matches, server creates the **token**
  - it's a string that is used to identify user to that user won't have to send id and pw with every request in future.

### 4. Generating token, and tell client to use that token for future requests.

**Server side:**

- Server creates a random token
- Server tells the client to store this token somewhere and use it for future request. Server does this by setting response header **Set-Cookie** along with body.

```
HTTP response looks like this:
====================================================================
HTTP/1.1 200 OK
Set-Cookie: access_token=xyztoken; Path=/; Domain=foo.com; expires=Thu, 01 Jan 2050 00:00:00 GMT;
--------------------------------------------------------------------<html>
<body>
<h1>Hello User!</h1>
(more user info)
  .
  .
  .
</body>
</html>
====================================================================
Set-Cookie header tells client to store access_token in cookie for path "/" and domain "foo.com" which "expires" on 1st day of 2050.
```

**Client side:**

- Client gets the response
- Client uses data (HTML) to render it on screen and value of set-cookie to set as a cookie.

### 5. User browses site as logged in user

**Client side:**

- user is logged in.
- Client has cookie. When user navigates, browser will send back the cookie to ther server by setting it to request header cookie

```
HTTP request looks like this:

GET https://www.foo.com/xyz HTTP/1.1
Cookie: access_token=xyztoken;

Client sends back that cookie to the server to identify current userid.
```

**Server side:**

- Server receives a request
- extracts access-token from cookie and searches for that token in database to see which user id it points to
- Once server has user id, it's easy to get all the information about the user and create specific HTML document for that user.
- If token doesn't match, server will redirect client to the login page, or show errors.
- While sending data back to the client, server doesn't have to send the Set-Cookie as a header again and again because client already have that cookie stored in a persistent storage.

### 6. Log out

**Client side:**

- When click on the logout, there's a separate route for logout (ex: /logout)
- Browser sends request to the server on that route with existing token set as a cookie.

**Server side:**

- extracts token, finds the userid and deletes the access token against that userid, and redirects user to login page.
- Now toke removed from database, so it tells client to remove that toke from cookie because that token doesn't exist anymore.
- While redirecting user to login page, server uses **Set-Cookie** header again, but sets access_token as empty string to tell browser to remove token from the cookie.

```
Set-Cookie: token=''; path=/; expires=Thu, 01 Jan 1970 00:00:00 GMT
```

Notes from class

인증: 회원가입과 로그인

인증이 왜 필요? 서비스를 누가 쓰는지, 어떻게 사용하는지, 추적이 가능하오록

인증에 필요한것: 아이디, 이메일, 비밀번호
