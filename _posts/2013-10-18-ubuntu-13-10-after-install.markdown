---
published: true
title: Ubuntu 13.10 after install
layout: post
tags: [linux,ubuntu]
categories: [linux,ubuntu]
permalink: /2013/10/ubuntu-13-10-after-install/
---
**Remove the overlay scrollbars:**

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

**Install Wine:**

```
sudo apt-get install wine
```

**Show user in top panel:**

```
gsettings set com.canonical.indicator.session show-real-name-on-panel true
```

**Disable crash reports:**

```
sudo gedit /etc/default/apport
```

and set **enabled=0**

**Restricted Extras:**

```
sudo apt-get install ubuntu-restricted-extras
```

**Disable Shoping lence:**
```
gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"
sudo apt-get remove unity-lens-shopping
```

**Disable Nautilus recursive search:**

```
sudo add-apt-repository ppa:dr3mro/personal
sudo apt-get update
sudo apt-get upgrade
nautilus -q
```


```
gsettings set org.gnome.nautilus.preferences enable-recursive-search false
```

**Nautilus file previewer:

```
sudo apt-get install gnome-sushi unoconv</code>
```

**Install Gimp:**

```
sudo apt-get install gimp gimp-data gimp-plugin-registry gimp-data-extras
```
