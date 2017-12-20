---
layout: post
title:  "[PHP] How to install PHP Accelerator in Xampp ?"
date:   2014-10-24
banner_image: PHP.jpg
tags: [PHP, Xampp]
---

The PHP Internationalization extension is used, amongst others, by Symfony (for validators).

This extension allows you to write codes like this one :

```php
$formatter = new NumberFormatter('en_US', NumberFormatter::DECIMAL);
echo $formatter->format(1234567.89); // 1,234,567.89

$formatter = new NumberFormatter('fr_FR', NumberFormatter::DECIMAL);
echo $formatter->format(1234567.89); // 1 234 567,89

$formatter = new NumberFormatter('en_US', NumberFormatter::CURRENCY);
echo $formatter->getTextAttribute(NumberFormatter::CURRENCY_CODE); // USD

$formatter = new NumberFormatter('pt_BR', NumberFormatter::CURRENCY);
echo $formatter->getTextAttribute(NumberFormatter::CURRENCY_CODE); // BRL
```

and so much more, including formatting of currency, number and date/time as well as UCA-conformant collations (customizable method to compare two strings).

To activate this extension in Xampp, just edit your php.ini (i.e. in *C:\xampp\php* directory) and remove the semicolon to uncomment this line :

    ;extension=php_intl.dll

Eventually don’t forget to restart Apache !
