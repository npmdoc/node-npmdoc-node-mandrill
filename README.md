# api documentation for  [node-mandrill (v1.0.1)](http://github.com/jimrubenstein/node-mandrill.git)  [![npm package](https://img.shields.io/npm/v/npmdoc-node-mandrill.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-node-mandrill) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-node-mandrill.svg)](https://travis-ci.org/npmdoc/node-npmdoc-node-mandrill)
#### A node.js wrapper for MailChimp's Mandrill API.

[![NPM](https://nodei.co/npm/node-mandrill.png?downloads=true)](https://www.npmjs.com/package/node-mandrill)

[![apidoc](https://npmdoc.github.io/node-npmdoc-node-mandrill/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-node-mandrill_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-node-mandrill/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-node-mandrill/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-node-mandrill/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Jim Rubenstein",
        "email": "jrubenstein@gmail.com",
        "url": "http://twitter.com/jim_rubenstein"
    },
    "bugs": {
        "url": "https://github.com/jimrubenstein/node-mandrill/issues"
    },
    "dependencies": {
        "request": ">= 2.9.100",
        "underscore": ">= 1.3.3"
    },
    "description": "A node.js wrapper for MailChimp's Mandrill API.",
    "devDependencies": {},
    "directories": {},
    "dist": {
        "shasum": "86580b7adbc152db3c658a864a7cec90f8d086fd",
        "tarball": "https://registry.npmjs.org/node-mandrill/-/node-mandrill-1.0.1.tgz"
    },
    "engines": {
        "node": ">= 0.8.2"
    },
    "homepage": "http://github.com/jimrubenstein/node-mandrill.git",
    "keywords": [
        "mandrill",
        "node mandrill",
        "mandrill api",
        "email",
        "send email",
        "email api",
        "mailchimp",
        "mailchimp api",
        "email mailchimp"
    ],
    "main": "mandrill.js",
    "maintainers": [
        {
            "name": "jrub",
            "email": "jrubenstein@gmail.com"
        }
    ],
    "name": "node-mandrill",
    "optionalDependencies": {},
    "readme": "# node-mandrill\n\nnode-mandrill is a node.js module designed to allow you to access MailChimp's\nMandrill API with minimal overhead.\n\nI designed node-mandrill so the only documentation you need, in addition to the\nMandrill API specification, is how to install node, how to install the module,\nand how to make a call.\n\n## Installation\n\nUsing [npm](http://npmjs.org):\n\n    npm install node-mandrill\n\nIf you don't have or don't want to use npm:\n\n    cd ~/.node_modules\n    git clone git://github.com/jimrubenstein/node-mandrill.git \n\n## Usage\n\nUsage is super simple.  To require the mandrill library and initialize it with\nyour account API key:\n\n    var mandrill = require('node-mandrill')('<Your Api Key Here>');\n\nTo make a call to the API, call the 'mandrill' function.  For example:\n\n    //send an e-mail to jim rubenstein\n    mandrill('/messages/send', {\n        message: {\n            to: [{email: 'git@jimsc.com', name: 'Jim Rubenstein'}],\n            from_email: 'you@domain.com',\n            subject: \"Hey, what's up?\",\n            text: \"Hello, I sent this message using mandrill.\"\n        }\n    }, function(error, response)\n    {\n        //uh oh, there was an error\n        if (error) console.log( JSON.stringify(error) );\n\n        //everything's good, lets see what mandrill said\n        else console.log(response);\n    });\n\n> ### Arguments\n> **mandrill(*string: api-endpoint*, *object: options*, *[function: callback]*)**\n>\n> **mandrill(*string: api-endpiont*, *function: callback]*)**\n>\n> **Api Endpoint**: The REST url for the API you want to access.  By default,\n> all requests are made requesting JSON as the response format.  If you'd like\n> to utilize a different format, you cann append '.yaml', '.php', or '.xml' to\n> the endpoint uri.  Node-mandrill will parse json responses and pass them to\n> the callback, but the other formats will be passed back as a string.\n>\n> **Options**: A javascript object defining the options as needed for the\n> requested API endpoint.  *note*: your API key is not required here, as the\n> module will automatically append it to your request.  However, you can\n> override your configured key by passing a value for a new key, using the\n> 'key' index of the options object.\n>\n> **Callback**: A function reference for a function to call upon completion of\n> the request.  It should accept 2 arguments.\n>\n> > **error**: if an error occurred (either with the HTTP request, or within\n> > the Mandrill API) the error will be passed back in this argument.  If there\n> > was no error, the value of error will be null.\n> >\n> > **response**: the response from Mandrill in the requested format.  JSON is\n> > requested by default, and is parsed into a native javascript object upon\n> > completion of the request.  If you choose to use one of the other formats\n> > (xml, yaml, php) the response will be passed back as a string to be used\n> > with your favorite parsers.\n> >\n\n## Requirements\n\n- A [Mandrill](http://mandrill.com/) account w/API key.\n- node.js v0.8.2+ (0.8.2 is the version I used to develop this module.  I'm\n  unsure if it will work with previous ones.  If you run a previous version, and\n  it works, let me know and I'll update this)\n- [request](https://github.com/mikeal/request/) 2.9.100+\n- [underscore](https://github.com/documentcloud/underscore/) 1.3.3+\n\n## Running Tests\n\nTests are written using [Jasmine](https://www.github.com/pivotal/jasmine), using\nthe [jasmine-node](https://github.com/mhevery/jasmine-node) binaries.  You'll\nneed to install jasmine-node to run the tests.\n\nOnce jasmine is installed, you will need to edit the 'spec/mandrill.spec.js'\nfile to reflect your Mandrill API key, and an email address to receive your\ntest e-mail on.  These two settings are at the top of the file.  Once they're\nin place, run your tests by doing:\n\n    $ ./test.sh\n\nOn your command line.  If you're running windows, well, sorry. ):\n\n## Question? Problems?\n\nIf you run into problems, have questions, or whatever else you can open an\nissue on this repository, or tweet me\n[@jim_rubenstein](http://twitter.com/jim_rubenstein).  If you'd like to submit\na patch, shoot me a pull request.  I'd like to keep this module simple, so if\nyou want to add all kinds of crazy functionality - you might want to fork.\nWhen in doubt, send a pull request - the worst that can happen is that I won't\nmerge it (:\n\n",
    "readmeFilename": "README.md",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/jimrubenstein/node-mandrill.git"
    },
    "version": "1.0.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module node-mandrill](#apidoc.module.node-mandrill)



# <a name="apidoc.module.node-mandrill"></a>[module node-mandrill](#apidoc.module.node-mandrill)



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
