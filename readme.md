# mdast-util-definitions [![Build Status](https://img.shields.io/travis/wooorm/mdast-util-definitions.svg)](https://travis-ci.org/wooorm/mdast-util-definitions) [![Coverage Status](https://img.shields.io/codecov/c/github/wooorm/mdast-util-definitions.svg)](https://codecov.io/github/wooorm/mdast-util-definitions)

Get a definition in `node` by `identifier`. Supports weird keys (like
`__proto__` or `toString`).

## Installation

[npm](https://docs.npmjs.com/cli/install):

```bash
npm install mdast-util-definitions
```

**mdast-util-definitions** is also available for [component](https://github.com/componentjs/component), [duo](http://duojs.org/#getting-started),
and for AMD, CommonJS, and globals ([uncompressed](mdast-util-definitions.js)
and [compressed](mdast-util-definitions.min.js)).

## Usage

```js
var remark = require('remark');
var definitions = require('mdast-util-definitions');

var ast = remark.parse('[example]: http://example.com "Example"');

var getDefinition = definitions(ast);

getDefinition('example');
// {type: 'definition', 'title': 'Example', ...}

getDefinition('foo');
// null
```

## API

### getDefinitionFactory(node): getDefinition

Create a cache of all `definition`s in `node`.

Parameters:

*   `node` (`Node`) — (Grand)parent of definitions.

Returns: `Function` — See [`getDefinition`](#getdefinitionidentifier)

### getDefinition(identifier)

Get a definition by `identifier`.

Parameters:

*   `identifier` (`string`) — Identifier of definition.

Returns: `Node?` — Definition, if found.

## License

[MIT](LICENSE) [@](https://github.com/) [Titus Wormer](http://wooorm.com)
