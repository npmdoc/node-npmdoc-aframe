# npmdoc-aframe

#### api documentation for  [aframe (v0.5.0)](https://aframe.io/)  [![npm package](https://img.shields.io/npm/v/npmdoc-aframe.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-aframe) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-aframe.svg)](https://travis-ci.org/npmdoc/node-npmdoc-aframe)

#### A web framework for building virtual reality experiences.

[![NPM](https://nodei.co/npm/aframe.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/aframe)

- [https://npmdoc.github.io/node-npmdoc-aframe/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-aframe/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-aframe/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-aframe/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-aframe/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-aframe/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "aframe",
    "version": "0.5.0",
    "description": "A web framework for building virtual reality experiences.",
    "homepage": "https://aframe.io/",
    "main": "dist/aframe-master.js",
    "scripts": {
        "browserify": "browserify src/index.js -s 'AFRAME' -p browserify-derequire",
        "build": "mkdirp build/ && npm run browserify -- --debug -t [envify --INSPECTOR_VERSION dev] -o build/aframe.js",
        "codecov": "codecov",
        "dev": "npm run build && cross-env INSPECTOR_VERSION=dev node ./scripts/budo -t envify",
        "dist": "node scripts/updateVersionLog.js && npm run dist:min && npm run dist:max",
        "dist:max": "npm run browserify -s -- --debug | exorcist dist/aframe-master.js.map > dist/aframe-master.js",
        "dist:min": "npm run browserify -s -- --debug -p [minifyify --map aframe-master.min.js.map --output dist/aframe-master.min.js.map] -o dist/aframe-master.min.js",
        "docs": "markserv --dir docs --port 9001",
        "ghpages": "ghpages -p gh-pages/",
        "lint": "semistandard -v | snazzy",
        "precommit": "npm run lint",
        "preghpages": "npm run dist && rimraf gh-pages && mkdirp gh-pages && cp -r {.nojekyll,dist,lib,examples,index.html,style} gh-pages/. 2>/dev/null || : && git checkout dist/ && replace 'build/aframe-master.js' 'dist/aframe-master.min.js' gh-pages/ -r --silent",
        "prerelease": "npm run dist && node scripts/release.js 0.4.0 0.5.0",
        "start": "npm run dev",
        "test": "karma start ./tests/karma.conf.js",
        "test:docs": "node scripts/docsLint.js",
        "test:firefox": "karma start ./tests/karma.conf.js --browsers Firefox",
        "test:chrome": "karma start ./tests/karma.conf.js --browsers Chrome"
    },
    "repository": "aframevr/aframe",
    "license": "MIT",
    "dependencies": {
        "browserify-css": "^0.8.2",
        "debug": "^2.2.0",
        "deep-assign": "^2.0.0",
        "document-register-element": "dmarcos/document-register-element#8ccc532b7",
        "envify": "^3.4.1",
        "load-bmfont": "^1.2.3",
        "object-assign": "^4.0.1",
        "present": "0.0.6",
        "promise-polyfill": "^3.1.0",
        "style-attr": "^1.0.2",
        "three": "^0.83.0",
        "three-bmfont-text": "^2.1.0",
        "tween.js": "^15.0.0",
        "webvr-polyfill": "dmarcos/webvr-polyfill#a02a8089b"
    },
    "devDependencies": {
        "browserify": "^13.1.0",
        "browserify-derequire": "^0.9.4",
        "browserify-istanbul": "^2.0.0",
        "budo": "^9.2.0",
        "chai": "^3.5.0",
        "chai-shallow-deep-equal": "^1.4.0",
        "chalk": "^1.1.3",
        "codecov": "^1.0.1",
        "cross-env": "^3.1.3",
        "exorcist": "^0.4.0",
        "ghpages": "0.0.8",
        "git-rev": "^0.2.1",
        "glob": "^7.1.1",
        "husky": "^0.11.7",
        "istanbul": "^0.4.5",
        "karma": "^1.3.0",
        "karma-browserify": "^5.1.0",
        "karma-chai-shallow-deep-equal": "0.0.4",
        "karma-chrome-launcher": "^2.0.0",
        "karma-coverage": "^1.1.1",
        "karma-env-preprocessor": "^0.1.1",
        "karma-firefox-launcher": "^1.0.0",
        "karma-mocha": "^1.1.1",
        "karma-mocha-reporter": "^2.1.0",
        "karma-sinon-chai": "^1.2.4",
        "lolex": "^1.5.1",
        "markserv": "0.0.20",
        "minifyify": "^7.3.3",
        "mkdirp": "^0.5.1",
        "mocha": "^3.0.2",
        "mozilla-download": "^1.1.1",
        "open": "0.0.5",
        "replace": "^0.3.0",
        "rimraf": "^2.5.4",
        "semistandard": "^9.0.0",
        "sinon": "^1.17.5",
        "sinon-chai": "^2.8.0",
        "snazzy": "^5.0.0",
        "too-wordy": "ngokevin/too-wordy",
        "uglifyjs": "^2.4.10",
        "write-good": "^0.9.1"
    },
    "link": true,
    "browserify": {
        "transform": [
            "browserify-css",
            "envify"
        ]
    },
    "semistandard": {
        "ignore": [
            "build/**",
            "dist/**",
            "examples/**/shaders/*.js",
            "**/vendor/**"
        ]
    },
    "keywords": [
        "3d",
        "aframe",
        "cardboard",
        "components",
        "oculus",
        "three",
        "three.js",
        "rift",
        "vive",
        "vr",
        "web-components",
        "webvr"
    ],
    "browserify-css": {
        "minify": true
    },
    "engines": {
        "node": ">= 4.6.0",
        "npm": "^2.15.9"
    },
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
