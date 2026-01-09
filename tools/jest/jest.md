# Initial Steps

- Install jest dependencies: npm i --save-dev jest @types/jest
- Update package.json to include the test script:

```json
"scripts": {
  "test": "jest",
  "build": "ncc build src/action.js --minify"
}
```

- Create a jest.config.js file:

```json
module.exports = {
  testEnvironment: 'node',
  collectCoverage: true,
  coverageReporters: ['text', 'lcov'],
  collectCoverageFrom: [
    'src/**/*.js',
    '!dist/**',
    '!node_modules/**'
  ]
}
```

- Add test directories and test files (example for the license-verifier):

```
__tests__/
  unit/
    shared-functions.test.js
    license-verifier.test.js
    action.test.js
  integration/
    license-checks.test.js
  fixtures/
    package-locks/
      good-licenses.json    # Package-lock with only acceptable licenses
      bad-licenses.json     # Package-lock with problematic licenses
      unknown-licenses.json # Package-lock with unknown licenses
    licenseignore/
      .licenseignore        # Sample ignore file for testing
```

- Create tests (example for the license-verifier):

```js
const core = require('@actions/core');
jest.mock('@actions/core');

describe('GitHub Action', () => {
  beforeEach(() => {
    jest.clearAllMocks();
    // Mock the core module functions
    core.getInput.mockImplementation((name) => {
      if (name === 'changedFiles') return 'file1 file2';
      if (name === 'deletedFiles') return 'deleted1';
      return '';
    });
  });

  test('should set output when unknown licenses are found', () => {
    // Mock implementation here
    // Verify core.setOutput was called with the correct values
  });

  // Additional tests for the action functionality
});
```

- GitHub workflow to run tests in CI:

```yaml
name: Tests

on:
  push:
    branches: [ main, release ]
  pull_request:
    branches: [ main, release ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci
      - run: npm test
```
