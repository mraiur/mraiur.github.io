---
published: true
title: Ubuntu Gnome + AppKeys bookmarked shortcut problem "fix"
layout: post
tags: [chrome,gnome,shortcut,ubuntu]
categories: [chrome,ubuntu]
permalink: /2015/06/291/
---
On Ubuntu Gnome 15.04 if chrome is bookmarked + AppKeys extensions.
Instead of focusing the opened chrome browser it opens new instance.

For the moment "a solution" is to delete the current "/usr/share/applications/google-chrome.desktop" shortcut file.
Because it replaces the changes in it.
Create a new file "/usr/share/applications/google-chrome-c.desktop" i put "-c" not to be replaced automatically.


{% highlight bash %}
[Desktop Entry]
Version=1.0
Name=Google Chrome
GenericName=Web Browser
Exec=/usr/bin/google-chrome-stable %U
Terminal=false
Icon=google-chrome
Type=Application
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
X-Ayatana-Desktop-Shortcuts=NewWindow;NewIncognito
## Custom
StartupWMClass=Google-chrome-stable

[NewWindow Shortcut Group]
Name=New Window
Exec=/usr/bin/google-chrome-stable
TargetEnvironment=Unity
## Custom
StartupWMClass=Google-chrome-stable

[NewIncognito Shortcut Group]
Name=New Incognito Window
Exec=/usr/bin/google-chrome-stable --incognito
TargetEnvironment=Unity
## Custom
StartupWMClass=Google-chrome-stable
{% endhighlight %}
