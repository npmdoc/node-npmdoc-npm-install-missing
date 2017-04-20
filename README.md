# npmdoc-npm-install-missing

#### api documentation for  npm-install-missing (v0.1.4)  [![npm package](https://img.shields.io/npm/v/npmdoc-npm-install-missing.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-npm-install-missing) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-npm-install-missing.svg)](https://travis-ci.org/npmdoc/node-npmdoc-npm-install-missing)

#### This module will attempt to reinstall any missing dependencies.  It can be called via the command line or used programmatically.

[![NPM](https://nodei.co/npm/npm-install-missing.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/npm-install-missing)

- [https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "npm-install-missing",
    "version": "0.1.4",
    "description": "This module will attempt to reinstall any missing dependencies.  It can be called via the command line or used programmatically.",
    "dependencies": {
        "async": "",
        "npm": ">=1.2.10"
    },
    "bin": {
        "npm-install-missing": "./bin/npm-install-missing"
    },
    "devDependencies": {
        "mkdirp": "",
        "mocha": ">=1.0.0",
        "node-assertthat": ""
    },
    "engines": {
        "node": ">= 0.9.x"
    },
    "main": "index.js",
    "scripts": {
        "test": "mocha -R spec"
    },
    "repository": {
        "type": "git",
        "url": "https://github.com/AlexCline/npm-install-missing"
    },
    "keywords": [
        "npm",
        "install",
        "missing",
        "retry",
        "module"
    ],
    "preferGlobal": true,
    "author": "Alex Cline <alex.cline@gmail.com>",
    "license": "Apache 2.0",
    "bugs": {
        "url": "https://github.com/AlexCline/npm-install-missing/issues"
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
