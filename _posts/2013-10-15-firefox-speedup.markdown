---
published: true
title: Firefox speedup
layout: post
tags: [firefox,speed,speedup,ubuntu,windows]
categories: [linux,windows,linux,firefox]
permalink: /2013/10/firefox-speedup/
---
First install ad-block plugin. If you really like a site make allow exception to help them with the banner profits :)

In address bar type : **about:config**

Modify these values:


# scroll step

**mousewheel.default.delta_multiplier_y** **= 300**

**
network.prefetch-next = false
browser.cache.disk.enable = false # Allow cache to be stored on your harddrive
browser.cache.memory.enable = false**

# animation

browser.tabs.animate = false

browser.download.animateNotifications = false

browser.preferences.animateFadeIn = false

browser.fullscreen.animate = 0

security.dialog_enable_delay = 0

# reader

reader.parse-on-load.enabled = false

reader.parse-on-load.force-enabled = false


browser.cache.disk.capacity = 358400

# prefetching next page

network.prefetch-next= false

# build-in video/chat
loop.enabled = false

# reader
reader.parse-on-load.enabled = false
# geolocation
geo.enabled = false
# allow multiple site requests

network.http.pipelining = true

network.http.proxy.pipelining = true

network.http.pipelining.aggressive = true

network.http.pipelining.ssl = true

network.http.pipelining.maxrequests = 64

network.http.max-connections = 900

network.http.max-persistent-connections-per-server = 12
# http cache
browser.cache.use_new_backend = 1

# search results in new tabs

browser.search.openintab = true

network.dns.disableIPv6 = true

**Add this values:**

nglayout.initialpaint.delay INTEGER 0

network.http.pipelining.firstrequest BOOLEAN TRUE


Linux: Smooth Scroll

general.smoothScroll.mouseWheel.durationMaxMS = 1000 [ Default 400 ]

Placeholder images:

browser.display.show_image_placeholders = false

In your firefox profile create **UserContent.css**
* In linux its something like **~/.mozilla/firefox/vdfhymz1.default**
where **vdfhymz1.default** is your firefox profile directory

```
/* Enable image placeholders */
@-moz-document url-prefix(http), url-prefix(file) {
  img:-moz-broken{
    -moz-force-broken-image-icon:1;
    width:24px;
    height:24px;
  }
}
```
