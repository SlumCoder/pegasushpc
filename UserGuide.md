# PegasusHPC is a High Performance Crawler #

Example: $java -Xmx4000m -jar pegaushpc.jar -t http://youtube.com/ -nt 1000 -ipBased -max 2000


## Usage ##
$java -xmX4000m -jar pegaushpc.jar -t {target} -nt {#threads} -max {#URIs} [-ipBased | -domainBased]

> -t {target} Complete URI of the targeted host i.e. http://google.com<br>
<blockquote>-nt {#threads} Number of threads to create. Suggested between 500-10000.<br>
-max {#URIs} Number of unique URIs to crawl.<br>
-<a href='ipBased.md'>ipBased</a> to follow links to different domain of the same server.<br>
-<a href='domainBased.md'>domainBased</a> to target a specific host or path<br></blockquote>

Use -h for to print this menu<br>
<br>
<br>
<br>
<h2>Requirements</h2>
Java 1.7<br>
<br>
<br>
<h2>Notes</h2>
If the queue is all time to 0, it probably means that networking I/O is bottleneck.<br>
Consider adapting the number of threads and total results if you use a <4GB ram machine