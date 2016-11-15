---
layout: post
title: How to get historical pricing data for Google Cloud Platform
---
I've found that Google Cloud Platform (GCP) makes it a bit easier to get current 
pricing data, compared to Amazon Web Services (AWS). That said, after much searching, 
I had not found a method to access historical pricing without having to go through the 
<a href="http://v3.cloudpricingcalculator.appspot.com/">pricing calculators they provide for older pricing</a>.  

Until now! You can access historical pricing by appending `'v3'`, `'v2'`, or `'v1'` to the front of the URL 
provided by Google for <a href="http://cloudpricingcalculator.appspot.com/static/data/pricelist.json">their current pricing.</a> 
Just a heads-up: you can access that link via HTTPS as well, and if you try to 
go from there to `v1..v3` in a web browser, you might get a security warning, as the older pricing 
is served only by HTTP. That said, if you're actually going to access the data, you're probably 
not cutting and pasting from a web browser :)  

Below is a simple example in Python for retrieving four sets of GCP pricing and storing it in a dict:  

```python
import requests

old_pricing = ['v1', 'v2', 'v3', 'current']
pricing = {}

for version in old_pricing:
    if version = 'current':
        url = 'http://cloudpricingcalculator.appspot.com/static/data/pricelist.json'
    else:
        url = ('http://{}.cloudpricingcalculator.appspot.com'
                '/static/data/pricelist.json').format(version)
    pricing[version] = requests.get(url).json()['gcp_price_list']

# then do whatever you want with the data 
```

That should work in Python 2.7.x and 3.x.  You can leave out `['gcp_price_list']` 
if you want to get metadata as well as the pricing data. And, unlike AWS, 
you don't need to build a scraper or have credentials to access this data, which is pretty sweet.