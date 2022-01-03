---
id: 9PcA6i4JTv4aNTSYvb837
title: XML
desc: ''
updated: 1641216544218
created: 1641216377391
---

## How to check if an XML sitemap contain some urls
https://stackoverflow.com/questions/15083200/how-to-check-if-the-sitemap-contain-some-urls


```python
from xml.etree import ElementTree as etree

urlset = etree.fromstring(xml)
if urlset.find('url') is None:
   print("sitemap has no urls") 

```


