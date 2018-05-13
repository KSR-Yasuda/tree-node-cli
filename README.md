# tree-node-cli

Lists the contents of directories in a tree-like format. Both CLI and Node APIs are provided.

## Installation

```bash
$ npm install tree-node-cli
# or globally
$ npm install -g tree-node-cli
```

## Example

```bash
$ tree -L 2 -I "node_modules"
tree-node-cli
├── LICENSE
├── README.md
├── __tests__
│   ├── __fixtures__
│   ├── __snapshots__
│   ├── fixtures
│   └── tree.test.js
├── bin
│   └── tree
├── jest.config.js
├── package.json
├── tree.js
└── yarn.lock
```

## CLI

```bash
$ tree [options] [path/to/dir]
```

**Note:** Use the command `treee` on Windows and Linux to avoid conflicts with built-in `tree` command.

The following options are available:

```bash
$ tree -h

  Usage: tree [options] [path/to/dir]

  Options:

    -V, --version             output the version number
    -a, --all-files           All files, include hidden files, are printed.
    -d, --dir-only            List directories only.
    -I, --exclude [patterns]  Exclude files that match the pattern. | separates alternate patterns. Wrap your entire pattern in double quotes. E.g. `"node_modules|lcov".
    -L, --max-depth <n>       Max display depth of the directory tree.
    --trailing-slash          Add a trailing slash behind directories.
    -h, --help                output usage information
```

## API

```js
const tree = require('tree');
const string = tree('path/to/dir', options);
```

`options` is a configuration object with the following fields:

| Field           | Default                    | Type    | Description                                                                                                                           |
| --------------- | -------------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `allFiles`      | `false`                    | Boolean | All files are printed. By default, tree does not print hidden files (those beginning with a dot).                                     |
| `dirOnly`       | `false`                    | Boolean | List directories only.                                                                                                                |
| `trailingSlash` | `false`                    | Boolean | Appends a trailing slash behind directories.                                                                                          |
| `exclude`       | `[]`                       | Array   | An array of regex to test each filename against. Matching files will be excluded and matching directories will not be traversed into. |
| `maxDepth`      | `Number.POSITIVE_INFINITY` | Number  | Max display depth of the directory tree.                                                                                              |

```js
const string = tree('path/to/dir'), {
  allFiles: true,
  exclude: [/node_modules/, /lcov/],
  maxDepth: 4,
});

console.log(string);
```

## License

MIT
