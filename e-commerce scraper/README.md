# How to make the most of your E-Commerce Scraper API free trial

E-Commerce Scraper API by Oxylabs is a public data scraper API tailored to retrieve real-time localized pricing and search information from most e-commerce sites at scale. In this tutorial, we’ll show how to get the most use out of a one-week free trial and help you decide whether this scraping solution serves your business’s needs.   

This guide will walk you through setting up Oxylabs’ E-Commerce Scraper API from scratch. Configuring it with a website of your choice will give a good grasp of the data quality, ease of integration, and whether this product is right for you. We will interact with the E-Commerce Scraper API using Python. For more programming languages and more complex examples, visit our [documentation](https://oxy.yt/LrU6). 

If you have discovered this tutorial before visiting our website, you can get a free trial by registering on the Oxylabs [dashboard](https://dashboard.oxylabs.io/en/), navigating to the E-Commerce Scraper API, and claiming your 7-day free trial. 

<br>
<img src="Screenshot%202022-03-28%20at%2013.23.24.png" width="400">

Shortly after, you will receive an email with a username and password. You will need these credentials to start using the E-Commerce Scraper API.

<img src="Web%20scraper%20email%20example.png" width="400">
<br>

## Setting up E-Commerce Scraper API

Now, let’s get into the concrete steps of integrating E-Commerce Scraper API:

1. Open up your IDE (integrated development environment).
2. Insert the credentials you received in your email:

```python
import requests

username = 'username'
password = 'password'
```

3. Define the ‘source’ and paste the URL of the e-commerce store you want to scrape. In this example, we use the books.toscrape.com product page. 

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal_ecommerce', #here we define source
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}
```

4. Post Payload to the endpoint as per the example below: [](https://realtime.oxylabs.io/v1/queries)

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal_ecommerce', 
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))
```

5. As E-Commerce Scraper API delivers a response in JSON, we need to access the ‘content’ key:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal_ecommerce',
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']
```

6. After this, we write HTML into the file:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal_ecommerce', 
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

After running the basic code, try adding parameters to retrieve more specified data. 

7. You can set up geo-location parameters that will help you collect geo-restricted data:

```python
'geo-location': 'United States'
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal_ecommerce', #here we define source
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html',
  'geo-location': 'United States'
}
 
response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
 ```
 
 8. If the website employs JavaScript, you should use the `render` parameter: 

```python 
'render': 'html'
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal_ecommerce', #here we define source
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html',
  'geo-location': 'United States',
  'render': 'html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

9. In case you want to automatically detect product data, try our adaptive parser:

```python
"parser_type": "ecommerce_product",
"parse": true
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal_ecommerce', #here we define source
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html',
  'geo-location': 'United States',

  'render': 'html',

  'parser_type': 'ecommerce_product',
  'parse': true
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

And this is it - now you know how to set up E-Commerce Scraper API and use it to your advantage. 

## Conclusion

As you can see from this detailed example, E-Commerce Scraper API is easy to integrate, but also it is packed with lots of valuable features. [Get in touch](https://oxy.yt/LrYs) with our sales team to further discuss your use case and find available targets for E-Commerce Scraper API.

