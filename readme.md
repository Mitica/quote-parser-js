# quote-parser

A node.js module for extracting quotes from text.

## Usage

```
var parser = require('quote-parser');

var quotes = parser.parse('text', 'ru');
```

## Example

```
var text = 'Plus "Nu cred ca este adevarat!", a spus Vlad Filat';
var lang = 'ro';
var quotes = parser.parse(text, lang, {
  persons: [{
    index: 41,
    id: 101
  }]
});

console.log(quotes);
// [ { index: 6,
//    text: 'Nu cred ca este adevarat!',
//    name: { index: 41, text: 'Vlad Filat' },
//    author: { index: 41, id: 101 } } ]
```

## API

### parser.languages();

Return a list of supported languages.

### parser.parse(text, lang[, options]);

Extract quotes from text.

- **text** (String) **required**;
- **lang** (String) **required** - two chars language code. Supported: ['ro', 'ru', 'bg', 'hu', 'it', 'cs', 'pl'];
- **config** (Object):
  - *minLength* (Number) - min quote length, default: 10;
  - *persons* ([Person]) - a list of persons, a person:
    - *index* (Number) **required** - index of the person name in text;

### Result

A list of quotes:

- **text** (String) - quote text;
- **index** (Number) - quote index in the text;
- **name** (Object) - an object where can be the name's author:
  - **text** (String);
  - **index** (Number);
- **author** (Object) - Author if founded.
