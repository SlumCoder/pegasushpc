"PegasusHPC is a High Performance Crawler" is a web crawler aimed at allowing a high throughput spidering and scalability by menas of parallel computing and optimized memory usage. Go to the [downloads](https://code.google.com/p/pegasushpc/downloads/list) section to get the last release.

The following benchmark was performed in my laptop (i7, 8GB ram and a 100mbps line).

![http://4.bp.blogspot.com/--r-jOmf4Rvs/UVJCK2_MGiI/AAAAAAAAEKo/hPNVZWQ7rE0/s1600/test.png](http://4.bp.blogspot.com/--r-jOmf4Rvs/UVJCK2_MGiI/AAAAAAAAEKo/hPNVZWQ7rE0/s1600/test.png)

  * Target: http://microsoft.com
  * Unique Analyzed URIs: 50019
  * Unique identified URIs: 66012
  * Execution time: 193s

  * Average Analysis ratio of **259 URIs/second**
  * Average unique URI finding ratio of **601 URIs/second**

The following figure shows a basic architecture diagram of PegasusHPC.

|![http://3.bp.blogspot.com/-sRqe5ldrRRY/UVIHqys0nGI/AAAAAAAAEKU/8L2bmyswHZI/s1600/24z9hco.png](http://3.bp.blogspot.com/-sRqe5ldrRRY/UVIHqys0nGI/AAAAAAAAEKU/8L2bmyswHZI/s1600/24z9hco.png)|
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|