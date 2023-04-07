# How to make the most of your SERP Scraper API free trial?

SERP Scraper API by Oxylabs is a public data scraper API tailored to retrieve real-time localized search results from major search engines. This tutorial will show how to get the most use out of a one-week free trial and help you decide whether this scraping solution serves your business’s needs.

This guide will walk you through setting up Oxylabs’ SERP Scraper API from scratch. As an example, we will scrape publicly available search results data from the largest search engine. Configuring this integration with our chosen search phrase will give you a good grasp of the data quality, ease of integration, and whether this product is right for you. We will interact with the SERP Scraper API using Python. For more programming languages and more complex examples, visit our [documentation](https://developers.oxylabs.io/scraper-apis/serp-scraper-api). 

If you have discovered this tutorial before visiting our website, you can get a free trial by registering on the Oxylabs [dashboard](https://dashboard.oxylabs.io/en/), navigating to the SERP Scraper API, and claiming your 7-day free trial. To start using SERP Scraper API, you first need to create an API user to authenticate it to SERP Scraper API.

## Setting up SERP Scraper API

Now, let’s get into the concrete steps of integrating SERP Scraper API:

1. Open up your IDE (integrated development environment).
2. Insert your Scraper API user credentials.

```python
import requests

username = 'username'
password = 'password'
```

3. Define the ‘source’ parameter and enter your preferred search phrase as a ‘query’ parameter value. In this example, we will use a ‘gaming chair’ as our search phrase.  

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #source indicates the scraper we will use
  'query': 'gaming chair'
}
```

4. Post Payload to the endpoint as per the example below: [](https://realtime.oxylabs.io/v1/queries)

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search',
  'query': 'gaming chair'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))
```

5. As SERP Scraper API delivers a response in JSON format, we need to access the ‘content’ key:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search',
  'query': 'gaming chair'
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
  'source': 'google_search',
  'query': 'gaming chair'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

After running the basic code, try adding parameters to retrieve more specified data. 

7. When scraping search engines, you may want to use a `geo_location` parameter to tailor your results to a specific location:

```python
'geo-location': 'New York,New York,United States'
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search',
  'query': 'gaming chair',
  'geo-location': 'New York,New York,United States'
}
 
response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
 ```
 
 8. If you want to receive search results, as if you’d be visiting the search engine using a specific device, you can add a `user_agent_type` parameter. For this example, we will set it to `mobile`. 

```python 
'user_agent_type': 'mobile'
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search',
  'query': 'gaming chair',
  'geo-location': 'New York,New York,United States',
  'user_agent_type': 'mobile'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

9. To receive structured data, you can add a `parse` parameter and set it to `True`:

```python
"parse": True
```

### Example:

```python
import requests
import json

username = 'username'
password = 'password'

payload = {
  'source': 'google_search',
  'query': 'gaming chair',
  'geo-location': 'New York,New York,United States',
  'user_agent_type': 'mobile',
  'parse': True
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

json_content = response.json()['results'][0]['content']

with open('parsed_website.json', 'w', encoding='utf-8') as output:
  json.dump(json_content, output, ensure_ascii=False, indent=4)
```

And this is it - now you know how to set up SERP Scraper API and use it to your advantage. 

## Conclusion

As you can see from this detailed example, SERP Scraper API is easy to integrate and packed with lots of valuable features. If you are considering using SERP Scraper API, you can select and purchase a subscription plan via self-service. [Get in touch](https://oxy.yt/LrYs) with our sales team if you need more assistance or have more ambitious plans for SERP Scraper API.

