# Awesome Twig

A curated list of useful Twig snippets.

If you want to contribute, you are highly encouraged to do so :)

## Table of Contents

- [Array, Mapping, and String](#array-mapping-and-string)
    - [Concatenate Data](#concatenate-data)
    - [First and Last Elements of an Array (or mapping, or string)](#first-and-last-elements-of-an-array-or-mapping-or-string)
    - [Limit the Length of a Text and Add Ellipsis](#limit-the-length-of-a-text-and-add-ellipsis)
- [Date and Time](#date-and-time)
    - [Current Date](#current-date)
- [Internationalization](#internationalization)
    - [Display Localized Date](#display-localized-date)
    - [Display Localized Currency Value](#display-localized-currency-value)
    - [Display Localized Number](#display-localized-number)
- [Loop](#loop)
    - [Filter Values Before Using them in a Loop](#filter-values-before-using-them-in-a-loop)
    - [Using the Keys of an Array](#using-the-keys-of-an-array)
- [Misc](#misc)
    - [Named Arguments for Filters](#named-arguments-for-filters)
- [Structure](#structure)
    - [Check If a Block Exists in Current Template](#check-if-a-block-exists-in-current-template)
- [Template](#template)
    - [Loading a Template From a String](#loading-a-template-from-a-string)
- [URL](#url)
    - [Generate URL-encoded Query String](#generate-url-encoded-query-string)
- [Variable](#variable)
    - [Check If a Variable is Defined](#check-if-a-variable-is-defined)
    - [Check for Empty Variable](#check-for-empty-variable)
    - [Using a Default Value If a Variable is not Defined](#using-a-default-value-if-a-variable-is-not-defined)

## Array, Mapping, and String

### Concatenate Data
```twig
{{ 'Name: ' ~ user.name }}
```

### First and Last Elements of an Array (or mapping, or string)
```twig
{{ todoList|first }}

{{ todoList|last }}
```
[[1]](http://twig.sensiolabs.org/doc/2.x/filters/first.html) [[2]](http://twig.sensiolabs.org/doc/2.x/filters/last.html)

### Limit the Length of a Text and Add Ellipsis
```twig
{{ text|length > 50 ? text|slice(0, 50) ~ '...' : text }}
```
or using the Twig Extension `truncate`:
```twig
{{ text|truncate(50, true) }}
```
[[1]](http://twig-extensions.readthedocs.io/en/latest/text.html#truncating-text)

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

## Loop

### Filter Values Before Using them in a Loop
```twig
{% for item in posts if item.published %}
    ...
{% else %}
    There are no items.
{% endfor %}
```

### Using the Keys of an Array
```twig
{% for key in array|keys %}
    ...
{% endfor %}
```

## Misc

### Named Arguments for Filters
```twig
{{ someVariable|convert_encoding(from='ISO-8859-1', to='UTF-8') }}
```

## Structure

### Check If a Block Exists in Current Template
```twig
{% if block("footer") is defined %}
    ...
{% endif %}

{% if block("footer", "common_blocks.twig") is defined %}
    ...
{% endif %}
```

## Template

### Fallback Templates

Include the first template that exists:
```twig
{{ include([
    'sites/' ~ site.slug ~ '/main.twig',
    'sites/' ~ site.slug ~ '/default.twig',
    'common/site_main.twig'
]) }}
```
or ignore if template is missing:
```twig
{{ include('sites/' ~ site.name ~ '/main.twig', ignore_missing=true) }}
```

### Loading a Template From a String
```twig
{{ include(template_from_string("Welcome {{ name }}")) }}
```
[[1]](http://twig.sensiolabs.org/doc/2.x/functions/template_from_string.html)

## URL

### Generate URL-encoded Query String
```twig
{{ {'param': 'value', 'foo': 'bar'}|url_encode }}
{# outputs "param=value&foo=bar" #}
```
[[1]](http://twig.sensiolabs.org/doc/2.x/filters/url_encode.html)

## Variable

### Check If a Variable is Defined
```twig
{% if someVariable is defined %}
    ...
{% endif %}
```

### Check for Empty Variable

Check if is not null, empty, or zero, and add a default value (if the variable is not defined)
```twig
{% if someVariable|default('someValue') %}
    ...
{% endif %}
```

### Using a Default Value If a Variable is not Defined
```twig
{{ name|default('John Smith') }}
```
