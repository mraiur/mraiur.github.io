---
published: true
title: Stream webcam video with raspberry
layout: post
tags: [subsonic,java]
categories: [linux,raspbian]
permalink: /2012/12/stream-webcam-video-with-raspberry/
---
Its not that hard to stream with your webcam but had to search to find the best solution and here it is.

[stream-cam](/2012/12/stream-webcam-video-with-raspberry/stream-cam)

run it with

```
./stream-cam.sh stop
```

{% highlight bash %}
./stream-cam.sh start ( start runs first stop to delete the stream file and kill the stuck process etc.. )
{% endhighlight %}


Default port is 8090. If you wish to change it first in the server.conf  ( Port 8090 ) and after that in the scripts/start.sh
( http://localhost:8090/webcam.ffm ).


*Tested on Raspberry Model B with 512MB ram
