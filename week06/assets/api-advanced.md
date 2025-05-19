# Week 6: Supplementary Information for Introduction to APIs

## HTTP: Client-Server Communication and the Request-Response Cycle

Before diving into APIs, it’s essential to understand how web communication works at its most basic level. The web runs on **HTTP (HyperText Transfer Protocol)**, a simple, text-based language that lets one computer or application (the **client**) ask another computer (the **server**) for data or actions. Whenever you browse a site or call a web service, your client sends an HTTP *request* and the server answers with an HTTP *response*.

An HTTP request consists of a **URL**—the address of the resource or endpoint you want—and an **HTTP method**, which tells the server what you’d like to do. The two most common methods are **GET** (to fetch data, like loading a webpage) and **POST** (to submit data, such as filling in a form). By combining the URL and method (e.g. `GET https://example.com/data`), the client makes its intentions clear.

When the server receives that request, it processes whatever work is needed—retrieving files, querying a database, or running a service—and then sends back a response. Each response begins with a **status code** (a number indicating success or failure, such as **200 OK** for success or **404 Not Found** when something is missing) followed by the **body** containing the actual data or content. For webpages this is usually HTML; for data services (APIs), it’s often JSON (JavaScript Object Notation).

This back-and-forth interaction is called the **request-response cycle**, and it’s entirely **stateless**—each request is handled on its own, with no memory of previous requests. That stateless design makes HTTP simple and highly scalable, allowing any client that speaks HTTP (from browsers to Python scripts) to interoperate with any server that understands HTTP. When you move on to APIs, you’ll leverage this same cycle to automate large-scale data retrieval and processing.

Listen to Alice Evans explain all things HTTP on [this](https://www.softwaresessions.com/episodes/how-http-works-with-julia-evans/) podcast.

## REST APIs: The Common Way to Communicate

When people talk about web APIs, they are often referring to **REST APIs**. **REST** stands for *Representational State Transfer*, which is a style of designing networked applications. You don’t need to remember the term, but here’s what it means in practice:

* **Uses HTTP:** REST APIs use the same protocol your web browser uses – HTTP. This means you’re often calling URLs (web addresses) just like loading a webpage, but instead of a webpage, you get data.
* **Endpoints and Resources:** In a REST API, different URLs (endpoints) represent different **resources** or services. For example, `GET https://api.openweathermap.org/data/2.5/weather?q=London` might retrieve weather data for London. Here, the endpoint `/data/2.5/weather` is a resource for weather info, and `q=London` is a parameter specifying the city.
* **HTTP Methods (Verbs):** REST APIs make use of HTTP methods such as:

  * **GET** – Retrieve data (for example, get information or fetch results; e.g., get the sentiment of a text or fetch a list of comments).
  * **POST** – Send data or create a new resource (for example, submit a new text to be analyzed, or add a new entry to a database via the API).
  * **PUT/PATCH** – Update an existing resource (for example, update a record in a database).
  * **DELETE** – Delete a resource.

  In our sentiment analysis example, you might use a GET request if the text is included in the URL or a POST request if you are sending the text in the request body. The key idea is that the method indicates what action you want to perform on the resource.
* **Stateless Communication:** REST APIs are **stateless**, meaning each request is independent. The server doesn’t retain information about your previous requests. This is like each request being a separate, self-contained transaction. For instance, if you call the sentiment analysis API twice with two different texts, the server doesn’t remember the first text when processing the second – you need to send all the information it needs each time. The stateless design makes it easier to scale and ensures that each server can handle any request without needing to know what came before.

REST APIs are popular because they are simple, scalable, and use existing web standards. Almost any programming environment can send HTTP requests, so REST makes it easy to interact with services from different languages and platforms. When you hear about APIs from providers like Google, Twitter, or OpenAI, they are usually implemented as RESTful APIs.

## Other API Styles: GraphQL and WebSockets

REST is the most common approach, but it’s not the only pattern you might encounter. Here are two other API styles, just for your awareness:

* **GraphQL:** GraphQL is an alternative approach where instead of multiple specific endpoints, you have a single endpoint that can handle flexible queries. You send a query describing exactly what data you want, and you get back precisely that data. This can reduce the number of requests needed for complex apps. For example, if a REST API required you to call one endpoint for user info and another for user posts, a GraphQL API could allow you to get both in a single request by specifying that in the query. It’s powerful for complex data fetching, but also a bit more advanced in usage. (In this course we won’t be using GraphQL, but it’s good to know it exists.)
* **WebSockets (Real-Time APIs):** A WebSocket provides a continuous two-way connection between client and server, allowing data to be sent in real time. This isn’t a request-response model; it’s more like an open channel. WebSockets are useful for applications like live chat, streaming data updates, or multiplayer games – anywhere you want instant, ongoing data flow. For instance, if you were tracking sentiment on a live stream of tweets, a WebSocket connection could stream new analyses continuously. This is more specialized, so we’ll stick to the request/response style in our work, but you might encounter WebSocket APIs in other contexts (e.g., real-time stock price feeds).

For most data analysis tasks (like fetching data or sending data for analysis), you’ll be using **REST APIs**, as they cover the majority of use cases and are easier to get started with.
