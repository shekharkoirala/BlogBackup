---
title: "Fujifilm_as_webcam"
date: 2023-05-24T22:07:46+01:00

draft: false
author: "shekhar"
authorLink: ""
description: ""
license: "MIT"
images: []
comments: true

hidefooter: true
tags: ["fujfilm", "xt4", "video", "webcam"]
categories: ["tools", "photography"]
featuredImage: ""
featuredImagePreview: ""


ShowBreadCrumbs: true
ShowPostNavLinks: false

featuredImage: ""
featuredImagePreview: ""

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: false

toc:
  enable: true
  auto: true
code:
  copy: true
  # ...
math:
  enable: true
  # ...
mapbox:
  accessToken: ""
  # ...
share:
  enable: true
  # ...
comment:
  enable: true
  # ...
library:
  css:
    # someCSS = "some.css"
    # located in "assets/"
    # Or
    # someCSS = "https://cdn.example.com/some.css"
  js:
    # someJS = "some.js"
    # located in "assets/"
    # Or
    # someJS = "https://cdn.example.com/some.js"
seo:
  images: []
---
### How to use your XT1/2/3/4 fujifilm camera as webcam for your ubuntu 22.04.

This is a simple guide to use your fujifilm camera as a webcam.


### Installation:

```shell script
sudo apt-get install gphoto2 v4l2loopback-utils v4l2loopback-dkms ffmpeg
```

modprobe setup

```shell script

sudo modprobe -r v4l2loopback
sudo modprobe v4l2loopback exclusive_caps=1 max_buffers=2 
```

check video sources

```shell script
ls -l /dev/video* 
```

Make sure there is no gphoto process already running:

```shell script
ps aux | grep gphoto 
```

check is camera is detected by gphoto2:

```shell scipt
gphoto2 --auto-detect 
```

start the webcam

```shell script
gphoto2 --stdout --capture-movie | ffmpeg -i - -vcodec rawvideo -pix_fmt yuv420p -threads 0 -f v4l2 /dev/video2 
```

Note: Huge thanks to : 
https://medium.com/nerdery/dslr-webcam-setup-for-linux-9b6d1b79ae22

