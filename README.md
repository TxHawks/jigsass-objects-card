# JigSass Objects Card
[![NPM version][npm-image]][npm-url]  [![Dependency Status][daviddm-image]][daviddm-url]   

 > An individual piece of distinguished UI

## Installation

Using npm:

```sh
npm i -S jigsass-objects-card
```

## Usage
First, you need to import JigSass Card:
```scss
@import 'path/to/jigsass-objects-card/scss/index';
```

And optionally [reconfigure](https://txhawks.github.io/jigsass-objects-card/#configuration) the defaults to your liking.

Like all other JigSass modules, JigSass Card does not automatically generate any CSS when imported.
In order to use its classes, you would have to first explicitly indicate your intention to use
them by enabling their generation in the associated [configurations map](#css-output), Leaving
us only with CSS we need:

All JigSass Card classes are responsive-enabled, using
[JigSass MQ](https://txhawks.github.io/jigsass-tools-mq/) and the breakpoints defined in the
[$jigsass-breakpoints](https://txhawks.github.io/jigsass-tools-mq/#variable-jigsass-breakpoints)
variable.

Based on enabled selectors in the [configuration map](#css-output), responsive modifiers are
generated according to the following logic:

```scss
.o-card[--modifier][-[-from-{breakpoint-name}][-until-{breakpoint-name}][-misc-{breakpoint-name}]]
```

So, assuming the `medium`, `large` and `landscape` breakpoints are defined in `$jigsass-breakpoints`
as `600px`, `1024px` and `(orientation: landscape)` respectively,


```scss
$jigsass-card-conf: (
  no-breakpoint: (
    raised: true,
  ),
  until-medium: (
    raised: true,
  ),
  from-large-when-landscape: (
    raised: true,
  ),
)
```

will generate the following classes:
  - `.o-card--raised`, which is not limited to any media-query.
  - `.o-card--raised--until-medium`, which will be in effect at
    `(max-width: 37.49em)` and will override styles in the default class
    until that point.
  - `.o-card--raised--from-large-when-landscape`, which will go into effect at
    `(min-width: 64em) and (orientation: landscape)` and will override styles
    in the default class under these  conditions.

## Documentation

The full documentation was generated using mdcss, and is available at 
[https://txhawks.github.io/jigsass-objects-card/](https://txhawks.github.io/jigsass-objects-card/)

## Contributing

It is a best practice for JigSass modules to *not* automatically generate css on `@import`, but 
rather have the user explicitly enable the generation of specific styles from the module.

Contributions in the form of pull-requests, issues, bug reports, etc. are welcome.
Please feel free to fork, hack or modify JigSass Card in any way you see fit.

#### Writing documentation

Good documentation is crucial for usability, scalability and maintainability. When 
contributing, please do make sure that both its Sass functionality (functions, mixins, 
variables and placeholder selectors), as well as the CSS it generates (selectors, 
concepts, usage exmples, etc.) are well documented.

Jigsass Card uses Jonathan Neal's [mdcss](//github.com/jonathantneal/mdcss).

When styles and documentation comments are not automatically generated by your module on `@import`,
please use the `sgSrc/sg.scss` file to enable their generation.

In addition, any file in `sgSrc/assets` will be available for use in the style guide.


## File structure
```bash
┬ ./
│
├─┬ scss/ 
│ └─ index.scss # The module's importable file.
│
├─┬ sgSrc/      # Style guide sources
│ │
│ ├── sg.sccs   # It is a best practice for JigSass 
│ │             # modules to not automatically generate 
│ │             # css and documentation on `@import.` 
│ │             # Please use this file to enable css
│ │             # and documentation comments) generation.
│ │
│ └── assets/   # Files in `sgSrc/assets` will be 
│               # available for use in the style guide
│
└─┬ docs/      # Documention
  │
  └── styleguide/ # Generated documentation 
                  # of the module's CSS
```

**License:** MIT



[npm-image]: https://badge.fury.io/js/jigsass-objects-card.svg
[npm-url]: https://npmjs.org/package/jigsass-objects-card

[daviddm-image]: https://david-dm.org/TxHawks/jigsass-objects-card.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/TxHawks/jigsass-objects-card
