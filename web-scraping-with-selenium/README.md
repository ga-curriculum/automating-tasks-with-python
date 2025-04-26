<h1>
  <span class="headline">Automating Tasks with Python</span>
  <span class="subhead">Web Scraping with Selenium</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to perform advanced web scraping techniques using Python and learn how to automate interactions with dynamic web pages using Selenium.

## What is web scraping?

Web scraping allows you to extract data from websites programmatically. Let's learn some advanced techniques to handle more complex scraping scenarios.

## Parsing HTML with BeautifulSoup and XPath

[BeautifulSoup](https://beautiful-soup-4.readthedocs.io/en/latest/) is a popular library for parsing HTML and XML documents. It provides a convenient way to navigate and search the parsed tree structure of a web page. XPath, on the other hand, is a query language used to navigate and select nodes in an XML or HTML document.

Here's an example of using BeautifulSoup and XPath to extract data from an HTML page:

```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com/products"
response = requests.get(url)
soup = BeautifulSoup(response.content, "html.parser")

# Extract product names using BeautifulSoup
product_names = [item.text.strip() for item in soup.select(".product-name")]

# Extract product prices using XPath
product_prices = [item.text.strip() for item in soup.xpath("//span[@class='product-price']")]
```

In this example, we use BeautifulSoup to parse the HTML content of a web page. We then use CSS selectors (`soup.select()`) to extract product names and XPath expressions (`soup.xpath()`) to extract product prices.

The combination of BeautifulSoup and XPath provides a powerful and flexible way to navigate and extract data from HTML documents.

## Handling dynamic web pages with Selenium

Some websites heavily rely on JavaScript to render content dynamically. In such cases, using BeautifulSoup alone may not be sufficient to extract the desired data. This is where [Selenium](https://www.selenium.dev/) comes into play.

Selenium is a tool that allows you to automate web browsers. It provides a way to interact with web pages programmatically, including clicking buttons, filling forms, and extracting data from dynamically generated content.

Here's an example of using Selenium to scrape data from a dynamic web page:

``` python
from selenium import webdriver
from selenium.webdriver.common.by import By

# Make sure you have the appropriate browser driver installed
driver = webdriver.Chrome()  
driver.get("https://example.com/dynamic-page")

# Wait for the dynamic content to load
driver.implicitly_wait(10)

# Extract data from the dynamically generated elements
product_names = [item.text for item in driver.find_elements(By.CSS_SELECTOR, ".product-name")]
product_prices = [item.text for item in driver.find_elements(By.XPATH, "//span[@class='product-price']")]

driver.quit()
```

In this example, we use Selenium to automate the Chrome browser (make sure you have the appropriate browser driver installed). We navigate to the dynamic web page using `driver.get()` and wait for the dynamic content to load using `driver.implicitly_wait()`. Then, we use Selenium's `find_elements()` method to locate and extract data from the dynamically generated elements using CSS selectors and XPath.

## Dealing with authentication and cookies

Some websites require authentication or use cookies to track user sessions. When scraping such websites, you must handle authentication and manage cookies to access protected content.

Here's an example of handling authentication and cookies using Selenium:

``` python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com/login")

# Fill in the login form
username_field = driver.find_element(By.NAME, "username")
password_field = driver.find_element(By.NAME, "password")
username_field.send_keys("your_username")
password_field.send_keys("your_password")

login_button = driver.find_element(By.CSS_SELECTOR, ".login-button")
login_button.click()

# Access protected content
driver.get("https://example.com/protected-page")
# Extract data from the protected page

driver.quit()
```

In this example, we use Selenium to navigate to a website's login page. We locate the username and password fields using `find_element()` and fill them with the appropriate credentials using `send_keys()`. Then, we find the login button and click it using `click()`. After successful authentication, we can access protected pages and extract data from them.

## Pagination and infinite scrolling

Some websites implement pagination or infinite scrolling to load content dynamically as the user scrolls down the page. When scraping such websites, you must handle pagination or simulate scrolling to load and extract all the desired data.

Here's an example of handling pagination using Selenium:

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com/paginated-data")

while True:
    # Extract data from the current page
    product_names = [item.text for item in driver.find_elements(By.CSS_SELECTOR, ".product-name")]

    # Check if there is a next page
    try:
        next_button = driver.find_element(By.CSS_SELECTOR, ".next-button")
        next_button.click()
    except:
        break

driver.quit()
```

Here we're using Selenium to navigate to a paginated web page. We extract data from the current page using `find_elements()`. Then, we check for a next page button and click it to load the next page. We repeat this process until there are no more pages to load. This way, we can extract data from all the paginated pages.

For infinite scrolling, you can use Selenium's `execute_script()` method to simulate scrolling and load more content dynamically. Here's an example:

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com/infinite-scroll")

while True:
    # Extract data from the currently loaded content
    product_names = [item.text for item in driver.find_elements(By.CSS_SELECTOR, ".product-name")]

    # Scroll to the bottom of the page to load more content
    driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

    # Check if there are no more products to load
    if len(driver.find_elements(By.CSS_SELECTOR, ".no-more-products")) > 0:
        break

driver.quit()
```

In this example, we use Selenium to navigate to a web page with infinite scrolling. We extract data from the currently loaded content using `find_elements()`. Then, we use `execute_script()` to scroll to the bottom of the page, triggering the loading of more content.

We repeat this process until there are no more products to load, which can be determined by checking for the presence of a specific element (for example, a "no more products" message).

## Strategies for effective web scraping

When performing web scraping, it's important to consider the following strategies to ensure a practical and ethical scraping process:

### Respect website Terms of Service and <code class="filepath">robots.txt</code>

Before scraping any website, review and comply with the website's Terms of Service and <code class="filepath">robots.txt</code> file.

The <code class="filepath">robots.txt</code> file specifies which parts of the website are allowed or disallowed for web crawlers. Respecting these guidelines is crucial to avoid legal issues and maintain a good relationship with website owners.

Explore more about the <code class="filepath">robots.txt</code> file [here](https://www.cloudflare.com/learning/bots/what-is-robots-txt/).

### Use delays and limit request rate

When scraping websites, it's important to introduce delays between requests to avoid overwhelming the server.

Sending too many requests in a short period can be perceived as aggressive and may lead to your IP address being blocked. Implement appropriate delays (for example, a few seconds) between requests to mimic human browsing behavior.

### Handle exceptions and errors gracefully

Web scraping can encounter various exceptions and errors, such as network issues, changes in website structure, or unexpected responses.

Implement proper exception handling to handle these situations gracefully. Log the errors, implement retry mechanisms, and provide informative error messages to assist in debugging and monitoring the scraping process.

### Store scraped data efficiently

When scraping large amounts of data, efficiently storing the scraped data is important. Consider using databases (for example, SQLite or MySQL) or file formats (like CSV or JSON) to store the data in a structured manner.

Efficient data storage allows for easy retrieval, analysis, and further processing of the scraped data.

### Monitor and maintain scraping scripts

Web scraping scripts may require maintenance over time as websites change. Regularly monitor your scraping scripts to ensure they are functioning as expected.

If a website's structure or layout changes, update your scraping code accordingly to adapt to the changes. Continuously test and validate the scraped data to ensure its accuracy and reliability.
