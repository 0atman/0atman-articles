---
title: Auto-start full-screen web page on Raspbian (Jessie) startup
layout: post
published_date: 2015-11-05 14:00:00 +0100
---

1 Install Chromium

2 Create a file called `~/.config/autostart/chromium.desktop` with the following contents:

```ini

[Desktop Entry]
Encoding=UTF-8
Name=Connect
Comment=Checks internet connectivity
Exec=/usr/bin/chromium-browser -incognito --kiosk YOUR_WEB_ADDRESS
```

3 Profit!
