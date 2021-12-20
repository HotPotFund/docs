# HotPot Fund Docs Website

This website is built using [gitbook](https://github.com), a modern static website generator.

# How to add a new page

Create a markdown file in its respective language directory.


## Installation gitbook and plugins

Install gitbook-cli
```console
npm install gitbook-cli -g
```

Install gitbook plugins
```console
gitbook install
```

## Local Development

```console
gitbook serve
```

This command starts a local development server and open up a browser window. Most changes are reflected live without having to restart the server.

## Build

```console
gitbook build
```

This command generates static content into the `_book` directory and can be served using any static contents hosting service.

# Other document generation methods

## How to generate markdown files from solidity Natspec comments

Install solidity doc gen
`npm install solidity-docgen`

Get the correct compiler version
`npm install -D solc-0.7@npm:solc@0.7.6`

Put the updated template `contract.hbs` in a /templates folder under the same directory as /contracts that you want to generate

Run `npx solidity-docgen --solc-module solc-0.7 -t ./templates`

## How to gernerate markdown files from typescript commments

`npm install --save-dev typedoc typedoc-plugin-markdown`

`typedoc --out <docs> src/index.ts`

see https://www.npmjs.com/package/typedoc-plugin-markdown for details

