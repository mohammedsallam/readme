## What does the application do?
CMS application management the content of your website,
like `Categories`, `Articles`, `Video categories`, `Videos`, `Photo galleries`, 
`Website galleries`, `Pages`, `Newsletters`, `Visitor message`, `Users`, and `Settings`. 

- [Requirements](#requirements)
- [Installation](#installation)
- [Structure](#structure)
- [DB design](#db-design)
- [Unit test](#unit-test)

## Requirements 
* PHP version: 7.2.5 at least 
* Laravel framework version: 7
* Database type: Mysql 
* Mysql version: 8.0.18
* Linux server

## Installation
* Read installation: [Here](installation.md).
  
## Structure
* Read structure: [Here](structure.md).

## DB design 
* Read [DB design](design.md).
  
## Unit test
* In TDD we use phpunit as unit test for each units to application.
* The unit testing falled into path `tests` directory which contains two directory.
* The first is `Feature` for test full feature for module.
* The second is `Unit` for test small unit for module.
* In common we use `Feature` directory for test application.
* Every module have test file for it.
* To run unit test execute the next command.
```php 
"./vendor/bin/phpunit" --filter UnitTestClassName
```
