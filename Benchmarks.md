<h3>
<b>Experimentation Results</b></h3>
In order to benchmarking the scalability of PegasusHPC, we carried out some experiments. The environment was the following one:<br />
<ul>
<li>Machine: Laptop i7 8GB ram.</li>
<li>Bandwidth: 100mbps</li>
<li>Target: <a href='http://microsoft.com'>http://microsoft.com</a></li>
<li>Max URls: 50000</li>
<li>#Worker Threads: 1024</li>
</ul>
<br />
As a result of the previous test, PegasusHPC wrote two files, the one with the results and a log file with the trace as:
<br />
```java

[main] INFO Target - protocol [http] host[microsoft.com] port[80] path[/]
[main] INFO Pegasus  - Targeting [http://microsoft.com/] with [1024]threads and stopping at[50000] results and targetting all subdomains
[main] INFO Dispatcher - [OK]Pool of 1024 threads successfully created, party started
[main] INFO Dispatcher - [OK]Current unique URIs[1] max urls[50000] idle threads [false] URIs queued [0].
[main] INFO Dispatcher - [OK]Current unique URIs[15] max urls[50000] idle threads [false] URIs queued [0].
[main] INFO Dispatcher - [OK]Current unique URIs[170] max urls[50000] idle threads [false] URIs queued [0].
...
[main] INFO Dispatcher - [OK]Current unique URIs[50019] max urls[50000] idle threads [false] URIs queued [66012].
[main] INFO Dispatcher - Results reached, stopping
[main] INFO DataStats - took [193]secs
[main] INFO DataStats - Analyzed [50019] unique pages
[main] INFO DataStats - Found [116031] unique pages
```
<br />
I made a simple script to parse the previous log file and allow gnuplot to easily get the data.<br />
```java

cut -d ' ' -f2- log.out  | grep Current |awk '{print $7 $9 $15}' | sed -e "s/URIs\\[//g" | sed -e "s/\\]urls\\[/ /g" |$sed -e "s/\\]\\[/ /g" | sed -e "s/\\].//g" &gt; clean.res
```
<br />
The gnuplot script I developed for the graph is the following one:
<br />
```java

set title "Target: http://microsoft.com/, Threads: 1024"
set terminal png
set output "plot.png"
set style data linespoints
set xlabel "Execution Time (seconds)"
set xrange [1:193]
set ylabel "Unique #URIs"
set yrange [1:80000]
set key left box
plot "clean.res" using 1 with linespoints ls 1 title "Analyzed URIs", "clean.res" using 3 with linespoints title "Queued URIs"
```
<br />
The chart that got generated as a result of the previous script running on the cleaned log file is shown in <i>Figure 3</i>.
<br />
<br />
<div>
<img src='http://4.bp.blogspot.com/--r-jOmf4Rvs/UVJCK2_MGiI/AAAAAAAAEKo/hPNVZWQ7rE0/s1600/test.png' />
</div>
<div>
<b>Figure 3</b>. PegasusHPC URIs Found per Second.</div>
<br />
<div>
If we do a simple computation of the previous numbers, we got an average Analysis ratio of <b>259 URIs/second</b> and an average unique URI finding ratio of <b>601 URIs/second</b>, which is not bad for a not so powerful laptop machine. More experiments will be carried out soon.</div>
<div>
<i><br /></i></div>
<div>
<i><br /></i></div>
<div>
<i><br /></i></div>
<div>
<i><br /></i></div>