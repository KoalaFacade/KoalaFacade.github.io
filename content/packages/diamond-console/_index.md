---
title: "Diamond Console"
date: 2023-01-30T19:30:27+07:00
draft: false
description: "Diamond Console is a package to handle your Domain Driven Design (DDD) based on Laravel"
tags: ["docs", "laravel", "ddd"]
keywords: ["ddd", "diamond console", "installation"]
---

{{< figure
    src="img/package/banner-diamond-dark.png"
    alt="Diamond Console"
    caption="Diamond Console"
    >}}

> Artisan command package to handle your Domain Driven Design project that suitable with Laravel base structures, made for comer of Domain Driven Design and advanced.

## Installation

Install Diamond Console with composer

```bash
 composer require koalafacade/diamond-console
```

then after Diamond Console installed run command below to set up your project.
The command below will generate namespace in composer and base directory structures.

```bash
 php artisan diamond:install
```

And then run this command for regenerate the autoload class.

```bash
composer dump-autoload
```

### Options

|      Name         |               Description                |
|:-----------------:|:----------------------------------------:|
| `--skip-refactor` | Skip refactor app path to Infrastructure |

---

## Commands
