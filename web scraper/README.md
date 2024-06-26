# Web Scraper API Free Trial Guide

[![Oxylabs promo code](https://user-images.githubusercontent.com/129506779/250792357-8289e25e-9c36-4dc0-a5e2-2706db797bb5.png)](https://oxylabs.go2cloud.org/aff_c?offer_id=7&aff_id=877&url_id=112)

Heavy duties are a specialty of the Oxylabs’ Web Scraper API. Through its use, accessing various public pages becomes a breeze.

In this tutorial, we will show you all the unique benefits and features you may want to explore to make the most out of your one-week free trial. We hope that you’ll have a much clearer view of whether this solution is for you by the end.

The primary focus of this tutorial will be to walk you through a straightforward example of how to set up a Web Scraper API from scratch. We highly recommend setting this up with a website of your choosing as this would allow you to test out the quality of data gathered, ease of integration, and most importantly, if this is a product that solves your needs and is worth investing time and money into. In this example, we’ll use Python with our Web Scraper API, though if you wish to see more cases that both use other languages and are more complex, please visit our [documentation](https://oxy.yt/xr1o).

If you have discovered this tutorial before visiting our website, you can get a free trial by registering on the Oxylabs [dashboard](https://dashboard.oxylabs.io/en/), navigating to the Web Scraper API, and claiming your 7-day free trial. To start using Web Scraper API, you first need to create an API user to authenticate it to Web Scraper API.

## How to set up Web Scraper API?

Let’s get into the concrete steps of integrating Web Scraper API:

1. Open up your IDE (integrated development environment). 
2. Insert your API user credentials.

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'
```

3. Define the ‘source’ and paste the URL of the website you want to scrape. In this example we use the [scraping sandbox](https://sandbox.oxylabs.io/products) search results page. 

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'universal', # Here we define the source
    'url': 'https://sandbox.oxylabs.io/products'
}
```

4. Post Payload to the [realtime endpoint](https://developers.oxylabs.io/scraper-apis/getting-started/integration-methods/realtime) as per example below:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'universal',
    'url': 'https://sandbox.oxylabs.io/products'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))
```

5. Web Scraper API response is in `JSON`, therefore we need to access the `content` key.

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'universal',
    'url': 'https://sandbox.oxylabs.io/products'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

html_content = response.json()['results'][0]['content']
```

6. And we write HTML into file:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'universal',
    'url': 'https://sandbox.oxylabs.io/products'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

html_content = response.json()['results'][0]['content']

with open('scraped_website.html', 'w') as output:
    output.write(html_content)
```

After running the basic function, try adding parameters that will retrieve more specified data. 

7. Geo-location parameters will help you collect geo-restricted data for the websites that the content is only available for certain countries. 

```python
    'geo-location': 'United States'
```

### Example:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'universal',
    'url': 'https://sandbox.oxylabs.io/products',
    'geo-location': 'United States'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

html_content = response.json()['results'][0]['content']

with open('scraped_website.html', 'w') as output:
    output.write(html_content)
```

8. If the website uses JavaScript, use `render` parameter: 

```python
    'render': 'html'
```

### Example:

```python
import requests

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'universal',
    'url': 'https://sandbox.oxylabs.io/products',
    'geo-location': 'United States',
    'render': 'html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

html_content = response.json()['results'][0]['content']

with open('scraped_website.html', 'w') as output:
    output.write(html_content)
```

9. If you want to retrieve parsed data, you can utilize the [Custom Parser](https://developers.oxylabs.io/scraper-apis/custom-parser) feature to define your own parsing logic.

### Example

```python
import requests, json

username = 'USERNAME'
password = 'PASSWORD'

payload = {
    'source': 'universal',
    'url': 'https://sandbox.oxylabs.io/products',
    'geo-location': 'United States',
    'parse': True,
    'parsing_instructions': {
        'products': {
            '_fns': [
                {
                    '_fn': 'xpath',
                    '_args': ['//div[contains(@class, "product-card")]']
                }
            ],
            '_items': {
                'Title': {
                    '_fns': [
                        {
                            '_fn': 'xpath_one',
                            '_args': ['.//h4/text()']
                        }
                    ]
                },
                'Price': {
                    '_fns': [
                        {
                            '_fn': 'xpath_one',
                            '_args': ['.//div[contains(@class, "price")]/text()']
                        }
                    ]
                }
            }
        }
    }
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json=payload, auth=(username, password))

parsed_content = response.json()['results'][0]['content']

with open('parsed_website.json', 'w') as output:
    json.dump(parsed_content, output, indent=4)
```

## Conclusion

We hope that this quick guide showed how truly effortless it is to set up our Web Scraper API and how the whole integration process functions.

As mentioned before, you can find popular scraping destinations in our [documentation](https://oxy.yt/xr1o). If you are considering using Web Scraper API, you can select and purchase a subscription plan via self-service. [Get in touch](https://oxy.yt/LrYs) with our sales team if you need more assistance or have more ambitious plans for Web Scraper API.








