# PHPUnit for GitHub actions
PHPUnit action for GitHub on PHP 8.0
This action triggers the PHPUnit

## Setup
Add these lines to your YAML config file
```yaml
- name: PHPUnit
  uses: chindit/actions-phpunit@master
```

**WARNING** : Be sure you have these lines **before** :
```yaml
- uses: actions/checkout@v2
- uses: php-actions/composer@v1
```

First line is used to checkout code and second line is used to install
composer dependencies.

Your workflow file should look like this:
```yaml
name: phpunit
on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Install dependencies
        run: composer install --prefer-dist --no-progress --no-suggest

      - name: PHPUnit
        uses: chindit/actions-phpunit@master
```

**TIP**: You can replace `@master` by `@1.0.0` or any specific version of this
package you'd like to use.