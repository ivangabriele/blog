---
layout: post
title:  "[npm] How to list installed packages without their dependencies ?"
date:   2016-01-01
banner_image: npm.jpg
tags: [npm]
---

    npm ls --depth=0

`depth` option allow you to control the dependencies tree depth you want so show.

Obviously you can apply that for globally instally packages :

    npm ls --depth=0 -g
