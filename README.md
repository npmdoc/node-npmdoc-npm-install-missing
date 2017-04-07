# api documentation for  [npm-install-missing (v0.1.4)](https://github.com/AlexCline/npm-install-missing#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-npm-install-missing.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-npm-install-missing) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-npm-install-missing.svg)](https://travis-ci.org/npmdoc/node-npmdoc-npm-install-missing)
#### This module will attempt to reinstall any missing dependencies.  It can be called via the command line or used programmatically.

[![NPM](https://nodei.co/npm/npm-install-missing.png?downloads=true)](https://www.npmjs.com/package/npm-install-missing)

[![apidoc](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-npm-install-missing_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-npm-install-missing/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Alex Cline",
        "email": "alex.cline@gmail.com"
    },
    "bin": {
        "npm-install-missing": "./bin/npm-install-missing"
    },
    "bugs": {
        "url": "https://github.com/AlexCline/npm-install-missing/issues"
    },
    "dependencies": {
        "async": "",
        "npm": ">=1.2.10"
    },
    "description": "This module will attempt to reinstall any missing dependencies.  It can be called via the command line or used programmatically.",
    "devDependencies": {
        "mkdirp": "",
        "mocha": ">=1.0.0",
        "node-assertthat": ""
    },
    "directories": {},
    "dist": {
        "shasum": "ca1c635341cef953cb2404e0db777e7c9e7e87a7",
        "tarball": "https://registry.npmjs.org/npm-install-missing/-/npm-install-missing-0.1.4.tgz"
    },
    "engines": {
        "node": ">= 0.9.x"
    },
    "homepage": "https://github.com/AlexCline/npm-install-missing#readme",
    "keywords": [
        "npm",
        "install",
        "missing",
        "retry",
        "module"
    ],
    "license": "Apache 2.0",
    "main": "index.js",
    "maintainers": [
        {
            "name": "alexcline",
            "email": "alex.cline@gmail.com"
        }
    ],
    "name": "npm-install-missing",
    "optionalDependencies": {},
    "preferGlobal": true,
    "readme": "npm-install-missing\n===================\n\nAn NPM module to reinstall missing dependencies.\n\n[![Build Status](https://travis-ci.org/AlexCline/npm-install-missing.png?branch=master)](https://travis-ci.org/AlexCline/npm-install-missing)\n\nI created this module after working on a project where deployments were failing due to missing module dependencies.  An 'npm install' would fail to install the required dependencies for an unknown reason and without error.  Since 'npm install' succeeds without error, there wasn't a way to tell if the dependency installation failed.\n\nWhen running 'npm install' for a second time on a project, npm will check the first level of modules to ensure they're installed, but not traverse the dependency tree to ensure all sub-module dependencies are installed.  You can run 'npm outdated' to check if modules are missing but npm won't install them for you.\n\nThis module combines 'npm outdated' and 'npm install' to install all missing dependencies within the dependency tree.\n\n\nInstallation\n------------\nTo be able to use this tool system-wide to install missing dependencies for all your node projects, install it globally.\n\n    npm install -g npm-install-missing\n\n\nUsage\n-----\nWithin your project directory:\n\n    npm-install-missing\n    \nThe script will check the current project directory for missing dependencies and install them automatically.\n\n\nDependencies\n------------\nThis module depends on the following modules:\n\n* async\n* npm\n\n\nTesting\n-------\nTo install the devDependencies and run the test framework:\n\n    cd npm-install-missing\n    npm install\n    npm test\n\n\nSupport\n-------\nPlease file tickets and issues using [GitHub Issues](https://github.com/AlexCline/npm-install-missing/issues)\n\n\nLicense\n-------\nCopyright 2013 Alex Cline alex.cline@gmail.com\n\nLicensed under the Apache License, Version 2.0 (the \"License\"); you may not use this file except in compliance with the License. You may obtain a copy of the License at\n\n   http://www.apache.org/licenses/LICENSE-2.0\nUnless required by applicable law or agreed to in writing, software distributed under the License is distributed on an \"AS IS\" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.\n",
    "readmeFilename": "README.md",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/AlexCline/npm-install-missing.git"
    },
    "scripts": {
        "test": "mocha -R spec"
    },
    "version": "0.1.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module npm-install-missing](#apidoc.module.npm-install-missing)
1.  [function <span class="apidocSignatureSpan">npm-install-missing.</span>getMissing (path, cb)](#apidoc.element.npm-install-missing.getMissing)
1.  [function <span class="apidocSignatureSpan">npm-install-missing.</span>init (cb)](#apidoc.element.npm-install-missing.init)
1.  [function <span class="apidocSignatureSpan">npm-install-missing.</span>installModule (module, cb)](#apidoc.element.npm-install-missing.installModule)



# <a name="apidoc.module.npm-install-missing"></a>[module npm-install-missing](#apidoc.module.npm-install-missing)

#### <a name="apidoc.element.npm-install-missing.getMissing"></a>[function <span class="apidocSignatureSpan">npm-install-missing.</span>getMissing (path, cb)](#apidoc.element.npm-install-missing.getMissing)
- description and source-code
```javascript
getMissing = function (path, cb){
  npm.load(function(err){
    if (err) throw err;
    npm.commands.outdated(function(err, data){
      if (err) throw err;
      var missing_modules = [];
      data.forEach(function(module){
        if(module[2] === undefined)
          missing_modules.push([module[1], module[3]]);
      });
      cb(missing_modules);
    });
  });
}
```
- example usage
```shell
...
    cb(err, module);
  });
});
};

NpmRetryInstall.init = function(cb){
var msg = [];
NpmRetryInstall.getMissing(process.cwd(), function(data){
  if(data.length > 0){
    console.log(data);

    async.map(data, NpmRetryInstall.installModule, function(err, result){
      result.forEach(function(module){
        msg.push(module[0] + "@" + module[1]);
      });
...
```

#### <a name="apidoc.element.npm-install-missing.init"></a>[function <span class="apidocSignatureSpan">npm-install-missing.</span>init (cb)](#apidoc.element.npm-install-missing.init)
- description and source-code
```javascript
init = function (cb){
  var msg = [];
  NpmRetryInstall.getMissing(process.cwd(), function(data){
    if(data.length > 0){
      console.log(data);

      async.map(data, NpmRetryInstall.installModule, function(err, result){
        result.forEach(function(module){
          msg.push(module[0] + "@" + module[1]);
        });
        return cb("Successfully installed: " + msg.join(', '));
      });
    } else {
      cb('No modules seem to be missing.  Huzzah!');
    }
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.npm-install-missing.installModule"></a>[function <span class="apidocSignatureSpan">npm-install-missing.</span>installModule (module, cb)](#apidoc.element.npm-install-missing.installModule)
- description and source-code
```javascript
installModule = function (module, cb){
  npm.load(function(err){
    if (err) throw err;
    npm.commands.install([module[0] + '@' + module[1]], function(err, data){
      cb(err, module);
    });
  });
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
