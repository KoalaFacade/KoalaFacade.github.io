---
title: "Forms"
date: 2023-01-31T19:30:10+08:00
draft: false
summary: "Put alert box to your forms area."
---

You can put alert box to your form area like the image above.

## Usage

```php
use KoalaFacade\FilamentAlertBox\Forms\Components\AlertBox;

AlertBox::make()
    ->label(label: 'Oops')
    ->helperText(text: 'please make a payment first.')
    ->icon(name: 'heroicon-o-exclamation')
    ->warning();
```

### Available Methods

These available methods you can use when defining alert box.

```php
  use Closure;
  /** Set alert title */
  function label(string $label): static;

  /** Set alert helper text */
  function label(string $text): static;

  /** define alert icon */
  function icon(string $name): static;

  /** define alert type */
  function primary(): static;
  function warning(): static;
  function success(): static;
  function danger(): static;

  /** hide alert box */
  function hidden(bool | Closure $condition = true): static;
  function hiddenOn(string | array $contexts): static;
```
