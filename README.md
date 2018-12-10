# 🇨🇭 js-swiss-cantons

<p align="center">
    <a href="https://travis-ci.org/stefanzweifel/js-swiss-cantons" title="Build Status">
        <img src="https://travis-ci.org/stefanzweifel/js-swiss-cantons.svg?branch=master" alt="Build Status">
    </a>
</p>

Find any Swiss canton by its abbreviation, name, or by the zipcode of any Swiss city. (This is a port of [php-swiss-cantons](https://github.com/stefanzweifel/php-swiss-cantons))

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

In order to work on this package you should have `npm`, `yarn` and `ava` installed globally.

```shell
git clone https://github.com/stefanzweifel/js-swiss-cantons.git
```

### Installing

You should install the package with `yarn` or `npm` in your project.

```shell
npm install @stefanzweifel/js-swiss-cantons
```

### Usage

Currently there are two methods available on the CantonManager Class: `getByAbbreviation` and `getByName`.

```javascript
import CantonManager from '@stefanzweifel/js-swiss-cantons';

let manager = new CantonManager();
let canton = manager.getByAbbreviation('SH');
let canton = manager.getByName('Schaffhausen');

console.log(
  canton.setLanguage('de').getName() // Schaffhausen
);
```

The ZipcodeSearch class can be used to find cantons by zipcode, be careful, it imports the entire zipcode dataset (~290kb).

```javascript
import ZipcodeSearch from '@stefanzweifel/js-swiss-cantons/src/ZipcodeSearch';

let search = new ZipcodeSearch();

let location = search.findbyZipcode('1201'); // Search by string
let location = search.findbyZipcode(8001); // Search by number

// Returns an object of the locality:
// {
//   "city_name": "Zürich",
//   "zipcode": 8001,
//   "community_name": "Zürich",
//   "canton": "ZH"
// }

You can also retrieve the whole dataset like this:
let locations = search.getDataSet();
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Tests are written with [ava](https://github.com/avajs/ava).

```shell
npm run test
```

## Deployment

```shell
npm update patch | minor | major
npm publish
```

## Built With

- [ava](https://github.com/avajs/ava) - Test Framework
- [nyc](https://github.com/istanbuljs/nyc) - Code Coverage

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/2media/js-regio-parameters/releases).

## Authors

- **Stefan Zweifel** - _Initial work_ - [stefanzweifel](https://github.com/stefanzweifel)

See also the list of [contributors](https://github.com/stefanzweifel/js-swiss-cantons/contributors) who participated in this project.

## Acknowledgments

- [php-swiss-cantons](https://github.com/stefanzweifel/php-swiss-cantons)
