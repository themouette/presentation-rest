# REST

---

# URL to identify resources

Collections:

* `/bananas`: collection of all available bananas.

Resources:

* `/bananas/joe`: _URI_ for banana "Joe"
* `/bananas/henry`: _URI_ for banana "Henry"

---

# Fetching a collection

> GET /bananas

## With pagination

> GET /bananas?offset=0&limit=10

## Filtering

> GET /bananas?color=yellow&size=small

## Select fields

> GET /bananas?fields=size,color,origin(country,town)

---

# Retrieve a resource

To `GET` a resource, is as simple as a `GET` request on the resource `URI`

    !html
    GET /bananas/henry HTTP/1.1
    Host: example.org
    Accept: application/json; q=1.0

> The response will be returned as `JSON`, if server can handle it, with a `200`
> status.

---

# Create a resource

`POST` data on collection root:

    !html
    POST /bananas HTTP/1.1
    Host: example.org
    Content-Type: application/json; charset=utf-8
    Content-Length: length
    Accept: text/html; q=1.0, text/*; q=0.8,

    {"color": "yellow", "size":"big"}

Server should return `201 Resource Created` response with one of following
content:

* `id` of the newly created resource
* `URI` of the resource
* the fully populated new resource

> When returning HTML content, use redirection to avoid resubmission.

---

# Update a resource

`PUT` (full update) or `PATCH` (partial update) data on the resource `URL`:

    !html
    PUT /bananas/12 HTTP/1.1
    Host: example.org
    Content-Type: application/json; charset=utf-8
    Content-Length: length
    Accept: text/html; q=1.0, text/*; q=0.8,

    {"color": "green", "size": "big"}

Server should return `200 OK` response with one of following
content:

* `id` of resource
* `URI` of the resource
* the fully populated resource

> When returning HTML content, use redirection to avoid resubmission.

---

# Delete a resource

A `DELETE` request on the resource `URI` is all it needs:

    !html
    DELETE /bananas/joe HTTP/1.1
    Host: example.org

You should receive a `204 No Content` empty response.

> When returning HTML content, use redirection to avoid resubmission.

---

# Mimic HTTP methods

Some clients can't use the whole set of HTTP verbs.

This is the case for browsers `form` tags.

As a workaround, we use an additional parameter: `method` (or `_method`).

> POST /bananas?method=put

---

# No HTTP verb fit your case ?

## What to do when there is no HTTP verb covering my case ?

> Have a look at [HTTP RFC](http://www.ietf.org/rfc/rfc2616.txt), there is some
more

> Is there a RFC covering my case ? ([WebDav](http://tools.ietf.org/html/rfc4918), ...)

## Implement a verb action on the collection

> POST /bananas/search

> POST /bananas/pay

> POST /bananas/split

