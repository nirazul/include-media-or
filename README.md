# DEPRECATION NOTICE
This project is no longer maintained.
Please use [@nirazul/scss-mq](https://github.com/nirazul/scss-mq) instead.

# include-media with nested feature queries and OR conditions

> Get the original **include-media** [here](https://github.com/eduardoboucas/include-media).

### Introduction

[**include-media**](https://github.com/eduardoboucas/include-media) simplifies the usage of media queries in Sass. However, media features could only be connected with an AND conjunction.
This fork enables the usage of nested lists of expressions that are connected with logical AND/OR conjunctions.

### Installation

- [Via npm:](https://www.npmjs.com/package/include-media-or) `npm install include-media-or`

### Usage

The `media` mixin can be used either as before with a list of arguments, or it can take a list as the only argument:

Lists with a list separator `space` are considered AND conjunctions

```
@include media(('<=phone' 'retina2x')) {
    color: red;
}
```

Lists with a list separator `comma` are considered OR conjunctions

```
@include media(('<=tablet', '>desktop')) {
    color: red;
}
```

Nested lists are resolved according to their hierarchy of braces

```
@include media(('<=tablet', (>phone retina2x))) {
    color: red;
}
```


### Custom media expressions

If you have customized the default media expressions map, please make sure that you update AND/OR conjunctions to the new format:

```
// OLD
$media-expressions: (
  'customRetina': '(min-resolution: 192dpi), (min-resolution: 2dppx)',
) !default;

// NEW
$media-expressions: (
  'customRetina': ('(min-resolution: 192dpi)', '(min-resolution: 2dppx)'),
) !default;
```
