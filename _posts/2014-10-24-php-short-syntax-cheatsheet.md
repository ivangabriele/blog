---
layout: post
title:  "[PHP] Short Syntax Cheatsheet"
date:   2014-10-24
banner_image: PHP.jpg
tags: [PHP]
---

Whether you need them to shorten your code, to understand code from someone else, or to use them to write your templates, here is a list of short syntax you can use in PHP :

<!--more-->

### Output : echo

```php
<?= $myVar ?>
```

which is similar to :

```php
<?php echo $myVar; ?>
```

### Ternary operator (conditional operator)

The combination of question mark and colon represent a specific syntax reserved to ternary operators.

```php
$myVar = (CONDITION) ? VALUE_1 : VALUE_2;

function $myFunction()
{
  return (CONDITION) ? VALUE_1 : VALUE_2;
}
```

which are respectively similar to :

```php
if (CONDITION) $myVar = VALUE_1;
else $myVar = VALUE_2;

function $myFunction()
{
  if (CONDITION) return VALUE_1;
  else return VALUE_2;
}
```

### Single conditional structures : *with an output*

This **only** works with `print` statement (because it actually always returns `1`, thus `== true`).

```php
(CONDITION) AND print(SOMETHING);
```

which is similar to :

```php
if (CONDITION)
{
  print(SOMETHING);
}
```

### Conditional structures : if … elseif … else

For pure PHP code :

```php
if (CONDITION 1):
  INSTRUCTION 1;
  INSTRUCTION 2;
elseif (CONDITION 2):
  INSTRUCTION 3;
else:
  INSTRUCTION 3;
endif;
```

For templates :

```php
<?php if (CONDITION 1): ?>
...
<?php elseif (CONDITION 2): ?>
...
<?php else: ?>
...
<?php endif ?>
```

### Conditional structures : switch … case

For templates :

Also, becareful with any space between the switch and the first case : this is really not a good idea to close PHP tag et reopen it between them. FYI: I really don’t like switches within templates.

```php
<?php switch($myVar):
case 1: ?>
...
<?php break;?>
<?php case 2: ?>
...
<?php break;?>
<?php endswitch;?>
```

### Loop structures : for / foreach / while

For templates :

```php
<?php for($i=0; $i<$i_max; $i++): ?>
...
<?php endfor ?>
```

```php
<?php while (CONDITION): ?>
...
<?php endwhile ?>
```

```php
<?php foreach($myArray as $value): ?>
...
<?php endforeach ?>
```
