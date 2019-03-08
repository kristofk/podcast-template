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

## Variables

**Site**

```sh
title: # Title of the podcast
language: # Language of the site and the podcast
author: # Hosts of the podcast
description: # Description and subtitle of the podcast
explicit: # yes or no wether the podcast is explicit.
itunesOwner: # Email address of the Apple ID from which this podcast will be uploaded to itunes.
category: # Category of the podcast in the iTunes directory
```

**Post Front Matter**

```sh
---
# Jekyll
layout: post
categories: [you can leave this empty]
episodeNumber: [num]

# Feed
title: # Episode title
date: # Release date. Format: yyyy-MM-dd HH:mm:ss Z
subtitle: # Short subtitle for the episode
explicit: # ["yes"/"no"]
duration: # The length of the episode. Format: hh:mm:ss
length: # The length of the episode. Format: seconds count
file: # URL to audio file
---
```

## Feed

Based on Accidental Tech Podcast's [feed](http://atp.fm/episodes?format=rss).

Validated by W3C [feed validator service](https://validator.w3.org/feed/#validate_by_input).

Additional reference from [Land of code](http://www.landofcode.com/rss-tutorials/rss-introduction.php).

### Feed structure

```sh
.
├── xml
├── rss
└── channel
    ├── title
    ├── link
    ├── lastBuildDate
    ├── language
    ├── generator
    ├── itunes:author
    ├── itunes:subtitle
    ├── itunes:summary
    ├── description
    ├── itunse:explicit
    ├── itunes:owner
    ├── itunes:category
    ├── itunes:image
    └── item # There is an item for each post.
        ├── title
        ├── dc:creator
        ├── pubDate
        ├── link
        ├── guid
        ├── description
        ├── itunes:author
        ├── itunes:subtitle
        ├── itunes:explicit
        ├── itunes:duration
        ├── itunes:image
        ├── content:encoded
        ├── enclosure
        └── media:content
```

### Feed tags

**Global**

| Name | Syntax | Description |
| ---- | ----------- | ----------- |
| xml | `<?xml version="1.0" encoding="ISO-8859-1" ?>` | Define XML standard. Non user editable. |
| rss | `<rss version="2.0">` | Define RSS standard. Non user editable.  |
| channel | `<channel>[...]</channel>` | Channel related tags go in here. |

**Channel**

| Name | Syntax | Description | Declaration |
| - | - | - | - |
| title | `<title>[…]<title>` | The name of the podcast. | `site.title` |
| link | `<link>[…]</link>` | The link to the website of the podcast. | `site.url` |
| lastBuildDate | `<lastBuildDate>[...]</lastBuildDate>` | The date and time of when the feed was last generated. | `site.time - date_to_rfc822` |
| language | `<language>[...]</language>` | The language of the podcast and the website. | `site.language` |
| itunes:author | `<itunes:author>[…]</itunes:author>` | The hosts of the podcast. | `site.author` |
| itunes:subtitle | `<itunes:subtitle>[…]</itunes:subtitle>` | The description of the podcast. | `site.description` |
| itunes:summary | `<itunes:summary>[…]</itunes:summary>` | The description of the podcast. | `site.description` |
| description | `<description>[…]</description>` | The description of the podcast. | `site.description` |
| itunes:explicit | `<itunes:explicit>[…]</itunes:explicit>` | yes or no wether the podcast is explicit or not. | `site.explicit` |
| itunes:owner | `<itunes:owner>`<br>`<itunes:name>[…]</itunes:name>`<br>`<itunes:email>[…]</itunes:email>`<br>`</itunes:owner>` | The account from whicht the podcast is going to be uploaded from. Should be the podcast email. The name and email is going to match. | `site.itunesOwner` |
| itunes:category | `<itunes:category text="[…]"/>` | The category of the podcast according to the iTunes directory. | `site.category` |
| itunes:image | `<itunes:image href="[…]"/>` | The link to the bix 1400x1400 artwork. This is the artwork.jpg file. | `site.url/assets/artwork.jpg` |
| item | `<item>[…]</item>` | Each individual episode has its own item. It contains all the information about the episode. | ` ` |

**Item**

| Name | Syntax | Description | Declaration |
| - | - | - | - |
| title | `<title>[…]<title>` | The title of the episode. | `post.title` |
| pubDate | `<pubDate>[…]</pubDate>` | The publication date and time of the episode. | `post.date - date_to_rfc822` |
| link | `<link>[…]</link>` | Link to the episode on the podcast website. | `site.url/post.url` |
| guid | `<guid isPermaLink="true">[…]</guid>` | Link to the episode on the podcast website. | `site.url/post.url` |
| description | `<description><![CDATA[[…]]]></description>` | The show notes for the episode. This is the body of the post itself. | `???` |
| itunes:author | `<itunes:author>[…]</itunes:author>` | The name of the podcast. | `site.title` |
| itunes:subtitle | `<itunes:subtitle>[…]</itunes:subtitle>` | A short excerpt from the episode. | `post.subtitle` |
| itunes:explicit | `<itunes:explicit>[…]</itunes:explicit>` | yes or no wether the episode is explicit or not. | `site.explicit` |
| itunes:duration | `<itunes:duration>[…]</itunes:duration>` | The length of the episode in the following format: `hh:mm:ss`. | `post.duration` |
| itunes:image | `<itunes:image href="[…]"/>` | The episode cover art. It is uniform across all episoded. If you want a unique image then encode it into the chapters. | `site.url/assets/small-artwork.jpg` |
| content:encoded | `<content:encoded><![CDATA[ ]]></content:encoded>` | The encoding of the show notes. |  |
| enclosure | `<enclosure url="[…]" length="[…]" type="audio/mpeg"/>` | The url to the audio file and its length in `number of seconds`. | `post.file`, `post.length` |
| media:content | `<media:content url="[…]" length="[…]" type="audio/mpeg" isDefault="true" medium="audio"/>` | The url to the audio file and its length in `number of seconds`. | `post.file`, `post.length` |


*Colon `:` is not allowed in Liquid so front matter like `itunes:explicit` is not possible.*
