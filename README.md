This is a backup of the source code for the NPM package [@diffblue/cover-client
](https://www.npmjs.com/package/@diffblue/cover-client)
# Diffblue Cover client library - Node.js API for Diffblue Cover

The Diffblue Cover client library provides a programmatic interface and CLI for communicating with the Diffblue Cover API.

## Installation

Using npm:

```bash
npm install @diffblue/cover-client
```

## Usage

To use Diffblue Cover to run an analysis and produce test files you will need to provide a JAR file of your compiled code and the path to a directory where you want test files to be written.

In Node.js (using promises):

```js
const Analysis = require('@diffblue/cover-client').Analysis;
const fs = require('fs');

const analysis = new Analysis('https://your-cover-api-domain.com');
const buildFile = fs.createReadStream('./build.jar');
const settings = { ignoreDefaults: true, phases: {}};
const options = { outputTests: './tests' };

analysis.run({ build: buildFile }, settings, options)
.then((results) => {
  console.log(`Produced ${results.length} tests`);
  console.log(`Test files written to ${options.outputTests}`);
});
```

In Typescript (using async/await):

```ts
import Analysis from '@diffblue/cover-client';
import * as fs from 'fs';

const analysis = new Analysis('https://your-cover-api-domain.com');
const buildFile = fs.createReadStream('./build.jar');
const settings = { ignoreDefaults: true, phases: {}};
const options = { outputTests: './tests' };

(async () => {
  const results = await analysis.run({ build: buildFile }, settings, options);
  console.log(`Produced ${results.length} tests`);
  console.log(`Test files written to ${options.outputTests}`);
})();
```

For more detailed usage, see the [programmatic interface documentation](docs/programmatic-interface.md).

## Full documentation

- [Programmatic interface](docs/programmatic-interface.md)
  - [Object orientated interface](docs/programmatic-interface.md#object-orientated-interface)
    - [Instantiation](docs/programmatic-interface.md#instantiation)
    - [Usage](docs/programmatic-interface.md#usage)
      - [Start an analysis (object orientated)](docs/programmatic-interface.md#start-an-analysis-object-orientated)
      - [Get analysis status (object orientated)](docs/programmatic-interface.md#get-analysis-status-object-orientated)
      - [Get analysis results (object orientated)](docs/programmatic-interface.md#get-analysis-results-object-orientated)
      - [Cancel an analysis (object orientated)](docs/programmatic-interface.md#cancel-an-analysis-object-orientated)
      - [Get API version (object orientated)](docs/programmatic-interface.md#get-api-version-object-orientated)
    - [Result pagination](docs/programmatic-interface.md#result-pagination)
    - [Lifecycle](docs/programmatic-interface.md#lifecycle)
  - [Low level bindings](docs/programmatic-interface.md#low-level-bindings)
    - [Start an analysis (low level)](docs/programmatic-interface.md#start-an-analysis-low-level)
    - [Get analysis status (low level)](docs/programmatic-interface.md#get-analysis-status-low-level)
    - [Get analysis results (low level)](docs/programmatic-interface.md#get-analysis-results-low-level)
    - [Cancel an analysis (low level)](docs/programmatic-interface.md#cancel-an-analysis-low-level)
    - [Get API version (low level)](docs/programmatic-interface.md#get-api-version-low-level)
    - [Low level options](docs/programmatic-interface.md#low-level-options)
      - [Ignore https rejection](docs/programmatic-interface.md#ignore-https-rejection)
  - [Combining results into test classes](docs/programmatic-interface.md#combining-results-into-test-classes)
    - [Generate a new test class](docs/programmatic-interface.md#generate-a-new-test-class)
    - [Merge results into an existing test class](docs/programmatic-interface.md#merge-results-into-an-existing-test-class)
- [Command line interface](docs/command-line-interface.md)
- [Tests and checks](docs/tests-and-checks.md)
  - [Linting](docs/tests-and-checks.md#linting)
  - [Unit tests](docs/tests-and-checks.md#unit-tests)
  - [CLI tests](docs/tests-and-checks.md#cli-tests)
  - [Copyright checker](docs/tests-and-checks.md#copyright-checker)
  - [License checker](docs/tests-and-checks.md#license-checker)
  - [Integration tests](docs/tests-and-checks.md#integration-tests)
    - [Mock API](docs/tests-and-checks.md#mock-api)
- [Release procedure](docs/release-procedure.md)
- [Utilities](docs/utilities.md)
  - [Create Release](docs/utilities.md#create-release)
  - [Changelog](docs/utilities.md#changelog)
- [Code standards](docs/code-standards.md)
  - [File naming](docs/code-standards.md#file-naming)
  - [Branches](docs/code-standards.md#branches)
  - [Coding style](docs/code-standards.md#style)
  - [Code documentation](docs/code-standards.md#code-documentation)
- [Contributing guidelines](docs/contributing-guidelines.md)

Copyright 2019 Diffblue Limited. All Rights Reserved.
