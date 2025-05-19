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

Great, I’ll put together a conceptual overview of how API client libraries (especially in Python, with a mention of R) work, including when and why you’d use them, and how they simplify HTTP requests behind the scenes. I’ll be back shortly with the draft section you can add to your markdown.

## API Client Libraries

When working with web APIs, you often have the choice of using **API client libraries** instead of crafting raw HTTP requests. An API client library (sometimes called an SDK or helper library) is a package provided in a specific programming language that wraps the API’s functionality in convenient functions or classes. In Python especially, many major services offer official or community-maintained libraries to simplify API usage. These libraries act as a language-specific abstraction layer over the API – they break the API’s usual language-agnostic nature to make the developer experience smoother. In practice, this means you can interact with the API using Python objects and methods, rather than manually formatting HTTP requests and parsing responses.

**Why use a client library?** Client libraries **simplify and reduce the code** you need to write for common API tasks. Instead of manually assembling URLs, query parameters, headers, and JSON payloads for each request, you can call a function or method provided by the library and let it handle those details. For example, a library might provide a method like `get_user_tweets("Alice")` or `openai.ChatCompletion.create(...)` – behind the scenes, that method will construct the proper HTTP request (with the correct endpoint and parameters), send it, and parse the result for you. In other words, the library **“abstracts away the HTTP requests and offers more convenient interfaces”** to work with the API. This abstraction typically covers:

* **Request formatting and transport:** The library builds the correct HTTP requests (URLs, methods, headers, body) and sends them using an HTTP client, so you don’t have to manually use tools like `requests` or `curl`. It also often manages details like authentication headers (API keys, tokens) for you after an initial setup.
* **Response parsing and serialization:** Data returned from the API (usually in JSON) is automatically parsed into Python data structures or objects. Similarly, when you provide data to send (like a dictionary or object), the library serializes it to JSON. This spares you from manual JSON formatting.
* **Error handling and reliability:** Good client libraries include error handling logic. They might raise clear exceptions for error responses (rather than you checking HTTP status codes yourself) and handle common issues like rate limiting or retries. This means your code can focus on **what** you want to do with the API, and the library handles the low-level communication details.
* **Idiomatic interface:** The library’s functions and classes are designed to feel natural in the given language. For instance, Python libraries will return Python objects (like dictionaries or custom classes) and use Python naming conventions. This makes the API **“simple and intuitive to use”** in that language, as opposed to treating everything as raw text or HTTP mechanics.

## Concrete Walkthrough: Using `soccerdata` to Fetch Arsenal’s 2023–24 Match Stats

Below is a simple, step-by-step recipe for pulling Arsenal’s match-by-match team statistics for the 2023–24 Premier League season from FBref, using the `soccerdata` Python client library. You never write raw HTTP requests—`soccerdata` handles those for you.

```
# 1. Install and import the library
#    Wraps FBref’s REST API in Python methods.
#    pip install soccerdata
import soccerdata as sd

# 2. Initialize the FBref data source
#    Specify the league and season you want.
fbref = sd.FBref(leagues="ENG-Premier League", seasons="2023-24")

# 3. Retrieve Arsenal’s match stats
#    Returns a pandas DataFrame of every fixture.
arsenal_stats = fbref.read_team_match_stats(team="Arsenal")

# 4. Inspect the resulting DataFrame
print(arsenal_stats.head())
```

### What just happened?

- **Abstraction over HTTP**  
  The `FBref` class builds the correct URLs, attaches any required headers or API keys, sends HTTP GET requests to FBref’s endpoints, and handles pagination and retries automatically.

- **Automatic data parsing**  
  JSON responses from FBref are converted into a pandas DataFrame for you—no manual `json.loads()` or DataFrame construction needed.

- **Error handling & reliability**  
  Common HTTP errors (e.g., timeouts, 404 Not Found) are wrapped in clear exceptions. Transient failures can trigger automatic retries, so your analysis code stays focused on insights, not networking glitches.

- **Idiomatic, Pythonic interface**  
  The library returns native Python objects (DataFrames, lists, dictionaries) and uses familiar method names, making the API feel intuitive and concise rather than a tangle of raw HTTP mechanics.

Under the hood, `soccerdata` still uses an HTTP client (like `requests`) to interact with the REST API. But by encapsulating all networking, authentication, and JSON-handling logic in a single `read_team_match_stats()` call, it lets you:

1. **Write clean, declarative code**  
2. **Develop faster with fewer bugs**  
3. **Focus on analysis and insights instead of HTTP details**

This pattern—installing a client library, instantiating a connector object, invoking a single method, and working with a DataFrame—is common across many Python APIs, from OpenAI to Google Cloud to GitHub. Once you understand it, you can apply it to virtually any web service.

**Client libraries in other languages:** While our focus is on Python, other programming languages provide similar conveniences. In R, for example, packages like **`httr`** (for making HTTP requests) and **`jsonlite`** (for parsing JSON) are commonly used to work with web APIs. Many APIs also have R packages or wrappers that function like client libraries, letting you call the API in one or two lines of R code. The core idea is the same: a client library abstracts the RESTful requests into native language functions. Regardless of language, using a client library means you can integrate an API into your data analysis or application with less hassle, letting you focus on interpreting results rather than the mechanics of HTTP.

In summary, API client libraries are your friend when working with web services. They provide a **convenient, high-level interface** for API interactions, handling the gritty details of HTTP communication, error handling, and data formatting behind the scenes. This allows you to use APIs more intuitively and efficiently as you analyze data or build applications, without reinventing the wheel for every API request.

[Please see our api-use.md file for fundamental information.](api-use.md)
