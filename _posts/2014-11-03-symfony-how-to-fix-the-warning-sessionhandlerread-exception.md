---
layout: post
title:  "[Symfony] How to fix the “Warning: SessionHandler::read()” exception ?"
date:   2014-11-03
banner_image: Symfony.png
tags: [PHP, Symfony]
---

If you too you got an error like this one :

    Warning: SessionHandler::read(): open(\xampp\tmp\sess_hagg7jkmp7l7fmh5ec4k6jmgu0, O_RDWR) failed: No such file or directory (2) in [...]\app\cache\dev\classes.php line 423

I let you know that you just have to add/change these 2 lines in *app/config/config.yml* to fix it :

```yml
framework:
    session:
        handler_id: session.handler.native_file
        save_path: "%kernel.root_dir%/sessions"
```
