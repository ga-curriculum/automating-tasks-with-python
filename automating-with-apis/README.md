<h1>
  <span class="headline">Automating Tasks with Python</span>
  <span class="subhead">Automating with APIs</span>
</h1>

**Learning objective:** By the end of this lesson, students will understand APIs and how they can be leveraged for automation.

APIs, or Application Programming Interfaces, are sets of rules and protocols that allow different software applications to communicate with each other. They provide a way for developers to access and interact with the functionality and data of various services and platforms.

# Introduction to APIs

Imagine you have a task that requires data from multiple sources or needs to interact with different services. Instead of manually gathering the data or performing the actions, you can use APIs to automate the process.

APIs act as intermediaries between different software systems. They define a set of endpoints, which are specific URLs that you can send requests to, along with the expected format of the request and response. By making API calls, you can retrieve data, send data, or trigger actions in the target system.

# RESTful APIs and HTTP Requests

One of the most common types of APIs is the RESTful API. REST stands for Representational State Transfer, and it's an architectural style for designing networked applications. RESTful APIs use standard HTTP methods to interact with resources.

The main HTTP methods used in RESTful APIs are:

- **GET:** Retrieves data from the server

- **POST:** Sends data to the server to create a new resource

- **PUT:** Updates an existing resource on the server

- **DELETE:** Deletes a resource from the server

When making API requests, you typically need to specify the endpoint URL, the HTTP method, and any required parameters or data in the request payload.

# Authentication and Authorization

Many APIs require authentication and authorization to ensure secure access to the resources. Authentication verifies the identity of the client making the request, while authorization determines what actions the authenticated client is allowed to perform.

Common authentication methods for APIs include:

- **API keys:** Unique identifiers that are passed with each request to authenticate the client

- **OAuth:** An authorization framework that allows third-party applications to obtain limited access to user accounts without sharing passwords

- **JSON Web Tokens (JWT):** Compact, self-contained tokens that securely transmit information between parties

When working with APIs, it's important to carefully handle authentication credentials and follow the API provider's guidelines for secure usage.

# Sending Requests and Handling Responses

To interact with APIs using Python, we can use the `requests` library. The `requests` library provides a simple and intuitive way to send HTTP requests and handle the responses.

Here's a basic example of sending a GET request to an API endpoint using requests:

``` python
import requests

url = "https://api.example.com/data"
response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    # Process the retrieved data
else:
    print("Request failed with status code:", response.status_code)
```

In this example, we import the `requests` library and specify the API endpoint URL. We then use `requests.get()` to send a GET request to the endpoint. The `response` object contains the server's response, including the status code and the response data.

We can check the `status_code` attribute to determine the success or failure of the request. A status code of 200 indicates a successful request. If the request is successful, we can access the response data using `response.json()`, which parses the JSON data into a Python dictionary or list.

# Working with JSON Data

JSON (JavaScript Object Notation) is a lightweight data interchange format commonly used in APIs. It represents data as key-value pairs and arrays, making it easy to work with in Python.

When sending data to an API, you often need to format it as JSON. The requests library allows you to pass a dictionary as the json parameter, and it automatically converts it to JSON format:

``` python
import requests

url = "https://api.example.com/data"
data = {"name": "John", "age": 30}
response = requests.post(url, json=data)
```

In this example, we send a POST request to the API endpoint, including a dictionary `data` as the JSON payload. The `requests` library takes care of converting the dictionary to JSON format before sending the request.

When receiving JSON data from an API response, you can use `response.json()` to parse the JSON data into a Python dictionary or list:

``` python
import requests

url = "https://api.example.com/data"
response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    # Process the retrieved JSON data
else:
    print("Request failed with status code:", response.status_code)
```

In this example, if the request is successful, `response.json()` parses the JSON data from the response into a Python dictionary or list, allowing you to access and manipulate the data easily.

# Exploring Popular APIs

There are numerous APIs available for various purposes, such as coding workflows, weather, geolocation, and more. Here are a few popular APIs you can explore for automation tasks:

- **GitHub API:** Allows you to interact with GitHub repositories, issues, pull requests, and more. You can automate repository management, retrieve repository information, and analyze code-related data.

- **Google Maps API:** Offers a wide range of geolocation services, including geocoding, reverse geocoding, directions, and distance calculations. You can automate tasks related to location data, such as converting addresses to coordinates or calculating travel distances.

- **OpenWeatherMap API:** Provides access to weather data for locations worldwide. You can automate weather-related tasks, such as retrieving current weather conditions, forecasts, and historical data.

- **Spotify API:** Allows you to interact with Spotify's music data and functionality. You can automate tasks like retrieving track information, creating playlists, and analyzing user listening habits.

These are just a few examples of the vast array of APIs available.
When working with APIs, make sure to review the API documentation, understand the authentication requirements, and adhere to the usage guidelines provided by the API provider.

By leveraging APIs, you can automate tasks that involve retrieving data from external sources, sending data to services, and interacting with various platforms.
APIs provide a powerful way to integrate different systems and streamline your automation workflows.