---
title: "Filament AlertBox"
date: 2023-01-30T19:32:23+07:00
draft: false
description: "Filament plugin for display a static alert box in your filament forms and widget."
tags: ['docs', 'laravel', 'filament']
keywords: ["filament", "alertbox", "installation"]
---

{{< figure
    src="img/package/banner-alertbox.webp"
    alt="Preview Filament AlertBox"
    caption="Preview Filament AlertBox"
    >}}

> Filament plugin for display a static alert box in your filament forms and widget.

## Installation

You can install the package via composer:

```bash
composer require koalafacade/filament-alertbox
```
After the package installed you can configure the tailwind.config.js to make Alert Box styles can fit with your styles
```js
module.exports = {
    content: [
        './vendor/koalafacade/filament-alertbox/**/*.blade.php'
    ]
}
```
then build the asset again. 
```bash
yarn build
```
or 
```bash
npm build
```
## Usage

For usage the alert box we've to kind of implementation you can go thru the page below.
