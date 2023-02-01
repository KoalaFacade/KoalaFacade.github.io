---
title: "Widget"
date: 2023-01-31T19:28:31+08:00
draft: false
summary: "Treat alert box as widget and can put anywhere in your Filament"
---

You can treat alert box as widget as well and put anywhere
that supported widget placements in your Filament project

## Usage

For implement alert box widget, you can create a widget as usual then inheritance our package class

```php
use KoalaFacade\FilamentAlertBox\Widgets\AlertBoxWidget;

use Closure;
use Illuminate\Support\HtmlString;

class YourWidgetTho extends AlertBoxWidget
{
    public string | Closure | null $icon = 'heroicon-o-exclamation';

    /** success, warning, danger, primary */
    public string $type = 'warning';

    public string | Closure | null $label = 'Oops!';

    public string | Closure | null | HtmlString $helperText = 'I love your mom';

    public function getHelperText(): string | HtmlString | null
    {
        return $this->helperText;
    }

    public function getLabel(): string
    {
        $label = $this->evaluate($this->label) ?? (string) Str::of($this->getName())
            ->beforeLast('.')
            ->afterLast('.')
            ->kebab()
            ->replace(['-', '_'], ' ')
            ->ucfirst();

        return $this->shouldTranslateLabel ? __($label) : $label;
    }
}
```
