# How to make the most of your E-Commerce Scraper API free trial

[![Oxylabs promo code](https://user-images.githubusercontent.com/129506779/250792357-8289e25e-9c36-4dc0-a5e2-2706db797bb5.png)](https://oxylabs.go2cloud.org/aff_c?offer_id=7&aff_id=877&url_id=112)

E-Commerce Scraper API by Oxylabs is a public data scraper API tailored to retrieve real-time localized pricing and search information from most e-commerce sites at scale. In this tutorial, we’ll show how to get the most use out of a one-week free trial and help you decide whether this scraping solution serves your business’s needs.   

This guide will walk you through setting up Oxylabs’ E-Commerce Scraper API from scratch. Configuring it with a website of your choice will give a good grasp of the data quality, ease of integration, and whether this product is right for you. We will interact with the E-Commerce Scraper API using Python. For more programming languages and more complex examples, visit our [documentation](https://oxy.yt/LrU6). 

If you have discovered this tutorial before visiting our website, you can get a free trial by registering on the Oxylabs [dashboard](https://dashboard.oxylabs.io/en/), navigating to the E-Commerce Scraper API, and claiming your 7-day free trial. To start using E-Commerce Scraper API, you first need to create an API user to authenticate it to E-Commerce Scraper API.

## Setting up E-Commerce Scraper API

Now, let’s get into the concrete steps of integrating E-Commerce Scraper API:

1. Open up your IDE (integrated development environment).
2. Insert your API user credentials.

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'
```

3. Define the ‘source’ and paste the URL of the e-commerce store you want to scrape. In this example, we use the Amazon search results page for the search term `shoes`; therefore, the source is set to `amazon`. 

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
  'source': 'amazon', # Here we define the source
  'url': 'https://www.amazon.com/s?k=shoes'
}
```

4. Post Payload to the endpoint as per the example below:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
  'source': 'amazon',
  'url': 'https://www.amazon.com/s?k=shoes'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))
```

5. As E-Commerce Scraper API delivers a response in JSON, we need to access the ‘content’ key:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
  'source': 'amazon',
  'url': 'https://www.amazon.com/s?k=shoes'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

html_content = response.json()['results'][0]['content']
```

6. After this, we write HTML into the file:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
  'source': 'amazon', # Here we define the source
  'url': 'https://www.amazon.com/s?k=shoes'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

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

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'amazon',
    'url': 'https://www.amazon.com/s?k=shoes',
    'geo-location': 'United States'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
    output.write(html_content)
 ```
 
 8. If the website employs JavaScript, you should use the `render` parameter: 

```python 
    'render': 'html',
```

### Example:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'amazon',
    'url': 'https://www.amazon.com/s?k=shoes',
    'geo-location': 'United States',
    'render': 'html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
    output.write(html_content)
```

9. In case you want to automatically detect and parse product data, add the `'parse': True` parameter to enable a dedicated parser. Visit [this link](https://faq.oxylabs.info/en/articles/8832750-what-are-oxylabs-dedicated-parsers) to find a list of all the dedicated parsers:

```python
    'parse': True
```

### Example:

```python
import requests, json

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'amazon',
    'url': 'https://www.amazon.com/s?k=shoes',
    'geo-location': 'United States',
    'render': 'html',
    'parse': True
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

parsed_content = response.json()['results'][0]['content']

with open ('parsed_website.json', 'w') as output:
    json.dump(parsed_content, output, indent=4)
```

If we don't have a dedicated parser for your target website, you can use the [Custom Parser](https://developers.oxylabs.io/scraper-apis/custom-parser) feature instead to define your own parsing logic. And this is it - now you know how to set up E-Commerce Scraper API and use it to your advantage. 

## Conclusion

As you can see from this detailed example, E-Commerce Scraper API is easy to integrate and packed with lots of valuable features. If you are considering using E-Commerce Scraper API, you can select and purchase a subscription plan via self-service. [Get in touch](https://oxy.yt/LrYs) with our sales team if you need more assistance or have more ambitious plans for E-Commerce Scraper API.

