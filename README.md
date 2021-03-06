# ngx-currency

[![Build Status](https://travis-ci.org/nbfontana/ngx-currency.svg?branch=master)](https://travis-ci.org/nbfontana/ngx-currency)
[![npm version](https://badge.fury.io/js/ngx-currency.svg)](http://badge.fury.io/js/ngx-currency)
[![devDependency Status](https://david-dm.org/nbfontana/ngx-currency/dev-status.svg)](https://david-dm.org/nbfontana/ngx-currency?type=dev)
[![GitHub issues](https://img.shields.io/github/issues/nbfontana/ngx-currency.svg)](https://github.com/nbfontana/ngx-currency/issues)
[![GitHub stars](https://img.shields.io/github/stars/nbfontana/ngx-currency.svg)](https://github.com/nbfontana/ngx-currency/stargazers)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/nbfontana/ngx-currency/master/LICENSE)

## Demo

https://nbfontana.github.io/ngx-currency/

## Table of contents

- [About](#about)
- [Installation](#installation)
- [Documentation](https://nbfontana.github.io/ngx-currency/docs/)
- [Development](#development)
- [License](#license)

## About

## Getting Started

### Installing and Importing

Install the package by command:

```sh
    npm install ngx-currency --save-dev
```

Import the module

```ts
import { NgxCurrencyModule } from "ngx-currency";

@NgModule({
    imports: [
        ...
        NgxCurrencyModule
    ],
    declarations: [...],
    providers: [...]
})
export class AppModule {}
```

### Using 

```html
    <input currencyMask [(ngModel)]="value" />
```

 * `ngModel` An attribute of type number. If is displayed `'$ 25.63'`, the attribute will be `'25.63'`.

### Options 

You can set options...

```html
    <!-- example for pt-BR money -->
    <input currencyMask [(ngModel)]="value" [options]="{ prefix: 'R$ ', thousands: '.', decimal: ',' }"/>
```  

Available options: 

 * `align` - Text alignment in input. (default: `right`)
 * `allowNegative` - If `true` can input negative values.  (default: `true`)
 * `decimal` -  Separator of decimals (default: `'.'`)
 * `precision` - Number of decimal places (default: `2`)
 * `prefix` - Money prefix (default: `'$ '`)
 * `suffix` - Money suffix (default: `''`)
 * `thousands` - Separator of thousands (default: `','`)

You can also set options globally...

```ts
import { NgxCurrencyModule } from "ngx-currency";
import { CurrencyMaskConfig, CURRENCY_MASK_CONFIG } from "ngx-currency/src/currency-mask.config";

export const CustomCurrencyMaskConfig: CurrencyMaskConfig = {
    align: "right",
    allowNegative: true,
    allowZero: true,
    decimal: ",",
    precision: 2,
    prefix: "R$ ",
    suffix: "",
    thousands: "."
};

@NgModule({
    imports: [
        ...
        NgxCurrencyModule
    ],
    declarations: [...],
    providers: [
        { provide: CURRENCY_MASK_CONFIG, useValue: CustomCurrencyMaskConfig }
    ],
    bootstrap: [AppComponent]
})
export class AppModule {}
```

## Quick fixes

### Ionic 2-3

Input not working on mobile keyboard

```html
<!-- Change the type to 'tel' -->
    <input currencyMask type="tel" [(ngModel)]="value" />
```

Input focus get hide by the mobile keyboard

on HTML
```html
<!-- Change the type to 'tel' -->
    <input currencyMask type="tel" [(ngModel)]="value" [id]="'yourInputId' + index" (focus)="scrollTo(index)" />
```

on .ts
```ts
import { Content } from 'ionic-angular';

export class...

    @ViewChild(Content) content: Content;
  
    scrollTo(index) {
        let yOffset = document.getElementById('yourInputId' + index).offsetTop;
        this.content.scrollTo(0, yOffset + 20);
    }
```

## Development

### Prepare your environment
* Install [Node.js](http://nodejs.org/) and NPM
* Install local dev dependencies: `npm install` while current directory is this repo

### Development server
Run `npm start` or `npm run demo` to start a development server on port 8000 with auto reload + tests.

### Testing
Run `npm test` to run tests once or `npm run test:watch` to continually run tests.

## License

MIT @ Neri Bez Fontana
