---
title: "Filament Crash"
date: 2023-01-30T19:32:30+07:00
draft: false
description: "Filament plugin to enforce your client to pay your project"
tags: ['docs', 'filament', 'laravel']
keywords: ["filament", "crash", "installation"]
---

> Filament plugin to enforce your client to pay your project
---

{{< alert >}}
  **Warning!** This package will make your client scream to you.
{{< /alert >}}

## Installation

```bash
composer require koalafacade/filament-crash
```

After the package installed it the package automatically serving the javascript to make blank your filament page base on due date your input.

## Usage

You need to set the due date and the deadline, you can put these in your .env

  ```env
DUE_DATE="2023-01-17"
DEADLINE_DAYS=10
  ```

those env will set the due date to 2023-01-17 and make the filament page will fully blank when 2023-01-27 (10 days after due date).
