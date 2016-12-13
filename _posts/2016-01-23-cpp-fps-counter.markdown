---
published: true
title: C++ FPS counter
layout: post
tags: [c,c++,fps]
categories: [c]
permalink: /2016/01/c-fps-counter/
---
There many angles to do this and here is mine.


{% highlight cpp %}
// include ctime to get timestamp
#include <ctime>

// define current fps
float framespersecond = 0;
// temporary counter for the current second
float frameCounter = 0;
// last update time as timestamp
int lastTime = 0;

void fps() {

	time_t  timev;
	int currentTimestamp = time(&amp;timev);

	if( lastTime != currentTimestamp){
		lastTime = currentTimestamp;
		framespersecond = frameCounter;
		frameCounter = 0;

		cout << currentTimestamp << " " << framespersecond << endl;
	} else {
		frameCounter++;
	}
}
{% endhighlight %}

And call fps() after each update in your main loop.
