---
layout: post
title:  "[PHP] How to install Intl extension in Xampp ?"
date:   2014-10-24
banner_image: PHP.jpg
tags: [PHP, Xampp]
---

To install PHP Accelerator in Xampp, you need first to go to your php.ini file (i.e. within C:xamppphp directory) and add this line inside Dynamic Extensions part :

Then you need :

1. to show you PHP configuration via the PHP function phpinfo()
2. to get 2 precious informations :<br>![]({{ "/images/posts/phpinfo-2.png" }})<br>![]({{ "/images/posts/phpinfo-1.png" }})<br>**x86** or **x64**, and **TS** (Thread Safe) or **NTS** (Non Thread Safe)
3. to download the corresponding DLL (including your PHP version) :<br>[http://pecl.php.net/package/APCu/4.0.8/windows](http://pecl.php.net/package/APCu/4.0.8/windows)<br>(PHP 7: [http://pecl.php.net/package/APCu/5.1.3/windows](http://pecl.php.net/package/APCu/5.1.3/windows))
4. to copy/paste the DLL file within your extensions directory
5. to edit your php.ini file (i.e. within C:xamppphp directory)
6. and add this line inside Dynamic Extensions part :

```
;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;

[...]

extension=php_apcu.dll
```

Eventually don’t forget to restart Apache !
