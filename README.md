Heatmaps

A very rudimentary system to serve out heatmaps in a web interface. Takes in simple CSV files, serves them out with a static HTML + Javascript web application, based on D3.

This is a very rough anonimized version of what I developed at $DAYJOB.

Assuming you have Python installed, simply run:

`$ ./serve.sh
$ open http://localhost:5137`

Screenshot:

![Screenshot](https://raw.githubusercontent.com/ojilles/heatmaps/master/screenshot.png)

Structure of the data
=====================

Files are stored on disk:

` datadir
	+ 1406419200  (timestamp of the day)
		<page.csv>`

Each page has the following information:

`requestday,pagetype,date,bucket,count
1406419200,Page4,1406419200,0.0,1
1406419200,Page4,1406419200,300.0,1`

The first timestamp is redundant, but signifies the date we're reporting on. The second one is a indentifier for the metric (in my case a particular webpage). Third column is the time of the request (quantized in 5 minute timeframes). Forth column is the latency (quantized in 25ms increments in my example). Last one is the number of occurences (in my case the number of requests that happened inside that 5 minute timeframe, within that 25ms latency window).
