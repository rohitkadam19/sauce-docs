---
id: testcafe
title: "Configuration Syntax: TestCafe"
sidebar_label: TestCafe
---

Please refer to the [Common Configuration Syntax Reference](/testrunner-toolkit/configuration#common-syntax-reference)for information regarding fields such as `apiVersion`, `kind`, and `sauce`.

## Example Configuration

```yaml
apiVersion: v1alpha
kind: testcafe
sauce:
  region: us-west-1
  concurrency: 1
  metadata:
    name: Testing Testcafe Support
    tags:
      - e2e
      - release team
      - other tag
    build: Release $CI_COMMIT_SHORT_SHA
suites:
  - name: "saucy test"
    browserName: "chrome"
    src:
      - "*/*.test.js"
    screenshots:
      takeOnFails: true
      fullPage: true
    platformName: "windows 10"
    env:
      hello: world
    speed: 1
    screenResolution: "1920x1080"
docker:
  fileTransfer: mount
testcafe:
  rootDir: tests/e2e/testcafe
  version: 1.11.0
```

## `testcafe`

__Description__: Details specific to the `testcafe` project configuration.

__Type__: *object*

__Example__:
```yaml
testcafe:
  rootDir: tests/
  version: ##VERSION##
```

### `version`

__Description__: Version of `testcafe` to use during tests

__Type__: *string*

__Example__:
```yaml
  version: ##VERSION##
```

### `rootDir`

__Description__: Absolute path to the test directory and related test files.

__Type__: *string*

__Example__:
```yaml
  rootDir: /path/to/tests/
```

## `suites`

__Description__: Field for defining test suite details such as the suite `name`, desired `browserName`, and test configurations.

__Type__: *object*

__Example__:
```yaml
suites:
  - name: "saucy test"
    platformName: "Windows 10"
    testMatch: '**/*.js'

    params:
      browserName: "firefox"
      headful: false
      slowMo: 1000
```

### `name`

__Description__: Name of the test suite.

__Type__: *string*

__Example__:
```yaml
  - name: "saucy test"
```

### `browserName`

__Description__: Name of desired browser. Although Testcafe supports triggering one test in multiple browsers, it is better here to split them into every suite to indicate each suite has its own test point.

__Type__: *string*

__Example__:
```yaml
  browserName: "chrome"
```

### `src`

__Description__: The explicit name, file glob, or location of the test files.

__Type__: *object*

__Example__:
```yaml
  src:
    - "tests/test_file1.test.js"
    - "tests/integrations"
    - "*/*.test.js"
```

### `env`

__Description__: Environment variables. Substituted variables like $MY_VAR can be expanded.

__Type__: *object*

__Example__:
```yaml
  env:
    hello: world
    foo: $MY_BAR
```

### `screenshots`

__Description__: Screenshots settings for testcafe. [See link in Testcafe](https://devexpress.github.io/testcafe/documentation/reference/configuration-file.html#screenshots).

__Type__: *object*

__Example__:
```yaml
  screenshots:
    takeOnFails: true
    fullPage: true
```

### `speed`

__Description__: Specifies the test execution speed. Tests are run at the maximum speed by default. You can use this option to slow the test down. Provide a number between 1 (the fastest) and 0.01 (the slowest).

__Type__: *float64*

__Example__:
```yaml
  speed: 1
```

### `platformName`

<p><small><Highlight color="#ad1415">sauce cloud only</Highlight></small><a href="/testrunner-toolkit/running-tests#test-on-sauce-labs">ℹ</a></p>

__Description__: Operating system on which the browser and test runs.

__Type__: *string*

__Example__:
```yaml
    platformName: "Windows 10"
```

### `testMatch`

__Description__: The explicit name, regex, or location of the test files.

__Type__: *string* | *regex*

__Example__:
```yaml
    testMatch: '**/*.js'
```

### `screenResolution`

<p><small><Highlight color="#ad1415">sauce cloud only</Highlight></small><a href="/testrunner-toolkit/running-tests#test-on-sauce-labs">ℹ</a></p>

__Description__: Set browser window screen resolution.

__Type__: *string*

__Example__:
```yaml
    screenResolution: "1920x1080"
```
