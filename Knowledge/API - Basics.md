> *What did the router say to the doctor? It hurts when IP.*

## API

API (*application programming interface*) is a general term used in all sorts of contexts. In an abstract sense, it describes a relationship between two actors. One actor provides a certain function, while the other wants to execute it without having to know what happens under the hood.

However, this article is not about interfaces or APIs in general. It will focus on web APIs.


## What is a web API, anyway?

The age-old analogy is that of a waiter and a customer. The customer orders a pizza from the waiter. The waiter disappears into the kitchen and 10 minutes later, he appears and delivers a pizza on a plate.

Now let's just exchange the roles and say:

- Waiter - web API
- Customer - any client (e.g., a mobile app or web app)
- Order - making an HTTP request
- Pizza - data
- Kitchen - a place where the magic happens (we don't care in this article)
- 10 minutes - response time

Those are all the ingredients you need to describe a slow, albeit functional web API. :)

## Let's ditch the analogies

The Wiki article on [web APIs](https://en.wikipedia.org/wiki/Web_API) states the following:

> A server-side web API is a programmatic interface consisting of one or more publicly exposed endpoints to a defined request–response message system, typically expressed in JSON or XML, which is exposed via the web—most commonly by means of an HTTP-based web server.

Let's dissect that quickly.

- Server-side - if I am a mobile app, I am a client, so the API is not on my side
- Web API - we've covered this
- Endpoints - parts of the API that provide different functions/data
- Request/response message system - you request something and get a response back
- JSON/XML - formats used to structure data in the request or the response
- HTTP - a popular request/response protocol widely used on the web that describes how requests and responses need to be formatted and executed

Let's expand our thinking a bit. This is how a typical flow would look like if we wanted to fetch all the Pokémon from a certain web API: 

- We would execute a GET HTTP request towards a certain endpoint that delivers Pokémon (e.g. `https://pokeapi.co/api/v2/pokemon`)
- It would do some magic...
- ...and return a response to us containing Pokémon, formatted in JSON

If you want to try it out, just open your trusty terminal and execute the following:
`curl https://pokeapi.co/api/v2/pokemon`


## HTTP Requests

I was a bit sly and mentioned a `GET` request without really explaining what it is. Let's dive deeper into HTTP requests.

Generally, these are the basic ingredients that make up an HTTP request:

- An HTTP method
- URI
- Headers
- Body

### HTTP methods

Each endpoint does not necessarily support all types of actions. Actions can be fetching data, creating data, updating data, deleting data, etc.

We call these actions HTTP methods and this is the full list:

* **GET** is used for retrieving data (a representation of a resource).
* **HEAD** is similar to GET, but it only fetches the header, not the body.
* **POST** is used for sending data.
* **PUT** is similar to POST, but it will update an existing resource instead of creating new ones.
* **PATCH** is used for partially updating a resource (e.g. just your name, but not your surname).
* **DELETE** is used for deleting a resource.
* **OPTIONS** is used for checking which methods are supported by a particular URL.
* **TRACE** echoes the received request.
* **CONNECT** is used for opening a tunnel (two-way communication).

See this [article on HTTP Request Methods](https://www.w3schools.com/tags/ref_httpmethods.asp) for more info.


### URI

The URI specifies the resource ("type of data" in layman's terms) you want to interact with.

For instance:

- URI for fetching all Pokémon: `https://pokeapi.co/api/v2/pokemon`
- URI for fetching the first Pokémon: `https://pokeapi.co/api/v2/pokemon/1`

#### Query params

Query params are additions to the URI via which you can pass some information so the response can be prepared for you in a specific way. It's like telling the waiter you want extra mozzarella on your pizza. :)

For instance:

- URI for fetching the first 100 Pokémon: `https://pokeapi.co/api/v2/pokemon?limit=100`

The query param here is `limit=100`. Consult your API docs to know when you can use which parameter and for what purpose.

### Request headers
Headers usually contain metadata like authorisation tokens, the content type, etc.

Here's an example of request headers:

```
Content-Type: application/json
User-Agent: PostmanRuntime/7.26.8
Accept: */*
Cache-Control: no-cache
Host: myapi.foo
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Length: 63
```

Read up on request headers [here](https://developer.mozilla.org/en-US/docs/Glossary/Request_header).

### Request body
When creating a resource using POST or other methods that send data, the request body will contain a full or partial representation of the resource to be created or updated. The body will often be specified in JSON or XML.

If you are not sending any data, the body should remain empty.

Here's an example of a request body in JSON:

```
{
	"name":  "John",
	"surname": "Doe"
	"occupation": "Tester"
}
```

### Example

Here's what a full request might look like:

```
POST /api/person HTTP/1.1
Content-Type: application/json
User-Agent: PostmanRuntime/7.26.8
Accept: */*
Cache-Control: no-cache
Host: myapi.foo
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Length: 63

{
	"name":  "John",
	"surname": "Doe"
	"occupation": "Tester"
}
```


## HTTP responses
A response is what you get back after making a request. Obviously. :)

Simply put, it consists of:

- A status code
- Headers
- Body

You're already familiar with headers and the body, so let's look closely into HTTP status codes.

### Status codes
Status codes are found at the very top of the response and they are issued to briefly signify what exactly happened with the request.

They usually have a three-digit code and a short description. There are five classes of status codes:

- **1xx** - informational response
- **2xx** - successfully processed
- **3xx** - redirection 
- **4xx** - client error
- **5xx** - server error

Here are some you might already be familiar with:

```
200 OK
201 Created
304 Not Modified
400 Bad Request
401 Unauthorized 
403 Forbidden
404 Not Found
405 Method Not Allowed
500 Internal Server Error
503 Service Unavailable
```

A list of all status codes can be found [here](https://httpstatuses.com/).

### Example

This is the response to `GET /api/v2/pokemon?limit=1` (some response headers are omitted for brevity):

```
HTTP/1.1 200 OK
Date: Fri, 09 Apr 2021 15:22:19 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
access-control-allow-origin: *
cache-control: public, max-age=86400, s-maxage=86400
etag: W/"a8-VCBC7cGvhjUog0edXFvoOrl6iko"

{"count":1118,"next":"https://pokeapi.co/api/v2/pokemon?offset=1&limit=1","previous":null,"results":[{"name":"bulbasaur","url":"https://pokeapi.co/api/v2/pokemon/1/"}]}
```

## Interacting with APIs

You can interact with APIs or even test them with a variety of tools:

- One of the most popular CLI tools is [cURL](https://curl.se/).
- If you prefer a GUI, we have a [nice tutorial on Postman](https://infinum.com/handbook/books/qa/tools/using-postman).
- Also, most programming languages come with tools that make interacting with APIs a breeze. The [requests](https://docs.python-requests.org/en/master/) lib for Python is one example.


---

![api.png](/img/api.png)




