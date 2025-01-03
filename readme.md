# Latte version branch 2.x maintained for PHP 8.4 onwards

>
> 💿 `composer require viaaurea/latte-v2`
>


Latte support for the v2 branch ended in 2023 with PHP 8.3 as the final supported PHP version.

We intend to support Latte v2 further, due to the fact that migration to Latte v3 is not trivial, if projects use custom tags (macros) heavily.

The intention is to support PHP 8.4+ without any deprecation warnings so that `E_ALL` can be used as the reporting level without issues.


## Installation

Replace the original Latte v2 by this package:

```
composer remove latte/latte
composer require viaaurea/latte-v2
```

You should see the original Latte being uninstalled.

>
> 💡
>
> This package _replaces_ the original Latte of version `2.11.*`,
> which means other packages that require `latte/latte:^2.11` will be content with `viaaurea/latte-v2`.
>


---

The original readme content follows.

---

---


[Latte: A Next-Generation Templating System for PHP](https://latte.nette.org)
=============================================================================

✅ The only truly secure templating system for PHP<br>
✅ You already know the syntax<br>
✅ It is really fast<br>
✅ Highly mature, stable, and widely used library

When it comes to templates, it pays off to be demanding and always expect nothing but the best. Latte is a true designer-friendly templating language. You will surely appreciate its intuitive syntax and enjoy many of its useful goodies.

[Documentation can be found on the website](https://latte.nette.org).


Support Latte
-------------

Do you like Latte? Are you looking forward to the new features?

[![Buy me a coffee](https://files.nette.org/icons/donation-3.svg)](https://github.com/sponsors/dg)

Thank you!
