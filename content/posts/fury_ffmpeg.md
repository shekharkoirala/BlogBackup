---
title: "Fast Fury and Fantastic .... The ffmpeg"
date: 2023-03-06T22:49:00Z

draft: false
author: "shekhar"
authorLink: ""
description: ""
license: "MIT"
images: []
comments: true

hidefooter: true
tags: ["ffmpeg", "developer", "video"]
categories: ["Work", "Tech Notes"]
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
### ffmpeg Recipes

A list of useful receipes when using ffmpeg. A dump for future references.



1. Extract frames from video: 
   ```shell script
    #!/bin/zsh

    # Find all .mp4 files in the current directory and store them in an array
    input_files=(*.mp4)

    # Loop through each input file
    for input_file in "${input_files[@]}"
    do
    # Get the path to the input file directory
    input_dir="$(dirname "$input_file")"

    # Create a folder for the input file images in the same directory as the input file
    folder_name="${input_file%.*}_images"
    output_dir="$input_dir/$folder_name"
    mkdir -p "$output_dir"
    
    # Extract images from the input file and save them to the folder
    ffmpeg -i "$input_file" -r 1 "$output_dir/output_%03d.png"
    done
    ```

2. combine video.mp4 and audio.mp4 to a single video. 
    ```shell script
    ffmpeg -i video.mp4 -i audio.mp4 -c copy -map 0:0 -map 1:1 -shortest combined.mp4
    ```
   
3. convert .h265 video to .h264
   ```shell script
   ffmpeg -i video1.mov -vcodec h264 -acodec mp2 video1.mp4
   ```

