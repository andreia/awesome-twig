# Awesome Twig

A curated list of useful Twig snippets.

If you want to contribute, you are highly encouraged to do so :)

## Table of Contents

- [Date and Time](#date-and-time)
    - [Current Date](#current-date)
- [Internationalization](#internationalization)
    - [Display Localized Date](#display-localized-date)
    - [Display Localized Currency Value](#display-localized-currency-value)
    - [Display Localized Number](#display-localized-number)
- [Structure](#structure)
    - [Check If a Block Exists in Current Template](#check-if-a-block-exists-in-current-template)

## Date and Time

### Current Date
```twig
{{ "now"|date("d/m/Y") }}
```

## Internationalization
[[1]](https://github.com/twigphp/Twig-extensions/blob/master/doc/intl.rst)

### Display Localized Date
```twig
{{ post.published_at|localizeddate('medium', 'none', locale) }}
```

### Display Localized Currency Value
```twig
{{ price|localizedcurrency('BRL') }}
```

### Display Localized Number
```twig
{{ product.quantity|localizednumber }}
```

## Structure

#### Check If a Block Exists in Current Template
```twig
{% if block("footer") is defined %}
    ...
{% endif %}

{% if block("footer", "common_blocks.twig") is defined %}
    ...
{% endif %}
```
