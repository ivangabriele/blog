---
layout: post
title:  "ShareCode"
date:   2015-04-13
banner_image: road.jpg
tags: [JS, PHP]
---

After starting JS and PHP courses at 3W Academy, I quickly needed something to live-type and share the corrected version of their exercises. Some tools exist but none of them matched my needs : share a code in which I can type and others can only watch and copy it. I then decided to create ShareCode, which is dead simple to use : the first to access a slug is the admin one (he can edit the code), all the next ones are read-only users.

As usually, you don’t have to install anything (not even a database), just download/clone it within an Apache-managed directory.

<!--more-->

### Contribution and Download

The repository is [available on Github](https://github.com/ivangabriele/ShareCode).

### Releases Notes

* v1.2.1
  * Fix code sharing problems
  * Cancels the scroll re-initializing for each reloading

* v1.2.0
  * CodeMirror v4 to v5
  * Autofocus when user is admin
  * Better code optimization and logic (less variables and parameters)
  * Tabulations indentation replaced by indentation with spaces (2)
  * Lose focus when “escape” key is pressed
  * Auto-clean all code files older than 7 days
  * Slug is now shown in the page title
  * A favicon

* v1.1.0
  * Safer server-side AJAX files (managing wrong slug and no existing file)
  * Complete reorganization of JS And PHP Ajax files
  * Better code optimization and logic
  * No more “last character” issue with fast-typing code (client-server double parameters comparison instead of one)
  * Usage of jquery-min instead of jquery (to lighten the global size)
  * Many more comments
