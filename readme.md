# fs-mapper

[![npm version](https://badge.fury.io/js/fs-mapper.svg)](https://badge.fury.io/js/fs-mapper)
[![Build Status](https://travis-ci.org/jsenjoy/fs-mapper.svg?branch=master)](https://travis-ci.org/jsenjoy/fs-mapper)
[![Coverage Status](https://coveralls.io/repos/jsenjoy/fs-mapper/badge.svg?branch=master&service=github)](https://coveralls.io/github/jsenjoy/fs-mapper?branch=master
)

Give a configure to modify path of the files matched.

## Usage

```js
const mapper = require('fs-mapper')

mapper.configure({
  '*.js': 'js/[dirname][filename]',
  'images/**/*.png': (dirname, filename) => `${dirname.replace(/images\//, '')}/${filename}`
})

mapper([
  'components/slide.js',
  'images/icons/person.png'
])
// {
//   'components/slide.js': 'js/components/slide.js',
//   'images/icons/person.js': 'icons/person.png'
// }
```

> Notice: dirname includes the last `/` or `\`，like: `a/b.js` => `{ dirname: 'a/', filename: 'b.js' }`, but: `a.js` => `{ dirname: '', filename: 'a.js' }``

## License

MIT
