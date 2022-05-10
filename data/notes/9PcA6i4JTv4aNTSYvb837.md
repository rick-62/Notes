
## How to check if an XML sitemap contain some urls
https://stackoverflow.com/questions/15083200/how-to-check-if-the-sitemap-contain-some-urls


```python
from xml.etree import ElementTree as etree

urlset = etree.fromstring(xml)
if urlset.find('url') is None:
   print("sitemap has no urls") 

```


