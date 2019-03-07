---
layout: page
title: readme
---

# podcast-template

This is template that can be used to host podcasts. This Jekyll powered website will generate the necessary rss feed for the podcast and if the listeners visit this website it can provide additional value like the about page or any ther custom pages, links and the bigger version of the the epiisode description.

## Directory structure

These are the folders and files you will work with in order to publish your podcast.

```sh
.
├── _posts
|   └── [date-episode-title].md
├── assets
|   └── artwork.jpg
├── audio-files
|   └── [date-episode-title].md
├── config.yml
└── favico.ico
```

## Episode Front Matter

```sh
---
layout: post
title: [episode title]
date: [yyyy-MM-dd HH:mm:ss Z]
categories: [you can leave this empty]
audio-file: [url to audio file]
---
```
