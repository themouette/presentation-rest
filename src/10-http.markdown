
# HTTP

---

# Client/Server Basics

A typical **client/server** request follows this pattern:

![](./images/client-server.png)

* **Client**: Hello _server_, give me the _resource_ at `URI`.

* **Server**: Here is the resource at `URI`:<br />

    `> Content`

For HTTP, a typical client is a **web browser**, and a server is a **web server**.

---

# HTTP Request

Request is made of:

* A **Unique Resource Identifier** (URI);
* An **HTTP verb** describing the action;
* Some **headers** describing requirements;
* A **request body** to send data.

Here is an example:

    !html
    GET /my/simple/uri?with-query-string HTTP/1.1
    Host: example.org
    Content-Type: text/plain; charset=utf-8
    Content-Length: length
    Accept: text/html; q=1.0, text/*; q=0.8,

    This is a content

---

# HTTP Response

Response is made of:

* Some **headers** to describe the content;
* The response **status**;
* The **content** of the request;

Here is an example:

    !html
    HTTP/1.1 200 OK
    Content-Type: text/html; charset=utf-8
    Content-Length: length

    <!DOCTYPE HTML>
    <html>
        <head>
        </head>
        <body>
            <h1>Hello world !</h1>
        </body>
    </html>

---

# HTTP Status 1/2

2XX: everything OK

* 200 OK
* 201 Resource created
* 204 No content

3XX: Redirections

* 301: Moved permanently
* 302: Found
* 304: not modified

---

# HTTP Status 1/2

4XX: Client error

* 400: Bad request
* 401: Unauthorized
* 403: Forbidden
* 404: Not found

5XX: Server error

* 500: Internal Server Error

---

# HTTP Verbs

An HTTP verb is an action to perform on a **resource** located at a given
**URI**:

* `GET`: retrieve a **resource** or a **collection of resources**;
* `POST`: create a new **resource**;
* `PUT`: update an existing **resource**;
* `DELETE`: delete a given **resource**;
* `PATCH`: partial update of a given **resource**.

---

# HTTP Parameters (1/2)

There are two types of parameters, **<span style="color:red">query string</span>**
and **<span style="color:green">request body</span>**.

<div class="highlight">
<pre>
GET /my/simple/uri?<span style="color:red">a=1&id=2</span> HTTP/1.1
Host: example.org
Content-Type: text/plain; charset=utf-8
Content-Length: length

<span style="color:green">b=3&city=paris</span>
</pre>
</div>

This is the two ways **client** can send data to server.

> By the way, **never trust user input**, **never!**

---

# HTTP Parameters (2/2)

Parameters can be provided in any format, so use `Content-Type` header.

## application/form-url-encoded

    foo=1&bar=some-value

## application/json

    {"foo":1,"bar":"some-value"}

## application/xml

    <params>
        <foo>1</foo>
        <bar>some-value</bar>
    </params>

---

# Content negotiation

Client use `Accept` header to tell server which format it underestand.

`Accept` is a list of formats the client understands:

* coma separated
* content type + understanding quality

**Example:**

<div class="highlight">
<pre>
POST /my/simple/uri?a=1&id=2</span> HTTP/1.1
Host: example.org
Content-Type: application/json; charset=utf-8
Content-Length: length
Accept: <span style="color:red">text/html; q=1.0</span>, <span style="color:green">text/&#42;; q=0.8</span>

{"foo":1,"bar":"some-value"}
</pre>
</div>

