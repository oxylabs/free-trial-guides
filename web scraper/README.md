# Web Scraper API Free Trial Guide

Heavy duties are a specialty of the Oxylabs’ Web Scraper API. Through its use, accessing various public pages becomes a breeze.

In this tutorial, we will show you all the unique benefits and features you may want to explore to make the most out of your one-week free trial. We hope that you’ll have a much clearer view of whether this solution is for you by the end.

The primary focus of this tutorial will be to walk you through a straightforward example of how to set up a Web Scraper API from scratch. We highly recommend setting this up with a website of your choosing as this would allow you to test out the quality of data gathered, ease of integration, and most importantly, if this is a product that solves your needs and is worth investing time and money into. In this example, we’ll use Python with our Web Scraper API, though if you wish to see more cases that both use other languages and are more complex, please visit our [documentation](https://oxy.yt/xr1o).

If you’ve already seen this tutorial before visiting our website, the easiest way to get a free trial is by visiting the [Web Scraper API](https://oxy.yt/ir0A) page and filling in the form.

<br>
<img src="/Web%20Scraper%20API%20free%20trial%20form.png" width="400">

After filling in the form, you will receive an email with a username and password. You will need these credentials to start using the Web Scraper API.

<img src="/Web%20scraper%20email%20example.png" width="400">
<br>

## How to set up Web Scraper API?

Let’s get into the concrete steps of integrating Web Scraper API:

1. Open up your IDE (integrated development environment). 
2. Add the credentials you received on the email:

```python
import requests

username = 'username'
password = 'password'
```

3. Define the ‘source’ and paste the URL of the Web store you want to scrape. In this example we use [](https://books.toscrape.com) product page. 

```python
username = 'username'
password = 'password'

payload = {
  'source': 'universal', #here we define source
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}
```

4. Post Payload to the endpoint as per example below: [](https://realtime.oxylabs.io/v1/queries)

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal', 
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))
```

5. Web Scraper API response is in `JSON`, therefore we need to access the `content` key.

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal',
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']
```

6. And we write HTML into file:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'universal',
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
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

username = 'username'
password = 'password'

payload = {
  'source': 'universal', #here we define source
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html',
  'geo-location': 'United States'
}
 
response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

8. If the website uses JavaScript, use `render` parameter: 

```python
'render': 'html'
```

### Example:

```python
import requests
username = 'username'
password = 'password'

payload = {
  'source': 'universal', #here we define source
  'url': 'https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html',
  'geo-location': 'United States',
  'render': 'html'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

## Conclusion

We hope that this quick guide showed how truly effortless it is to set up our Web Scraper API and how the whole integration process functions.

As mentioned before, you can find popular scraping destinations in our [documentation](https://oxy.yt/xr1o). Get in touch with our Sales team to further discuss your use cases and what unique targets our Web Scraper API could be used for.








