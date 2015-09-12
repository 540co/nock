# AngularJS Record $httpBackend

This project was forked from https://github.com/pgte/nock to change the nock.record.rec() output to create $httpBackend commands for AngularJS unit tests.

Minimal testing has been done at this point.  

Depending on how this hack evolves, it will most likely be copied into a different repo in the future.


## Install

- Download the repo and manually load via npm

```

npm install ./nock

```

## Example of how I am using

> You will need to also `npm install request` for this example

```

var nock = require('nock');
var request = require('request');

nock.recorder.rec();

var opt = {};
opt.url = "https://dre.540.co/api/reactions";
opt.qs = {"limit" : 5};
opt.method = "GET";
opt.headers = {};
opt.json = true;

request(opt);

var opt = {};
opt.url = "https://dre.540.co/api/searches";
opt.qs = {"limit" : 5};
opt.method = "GET";
opt.headers = {};
opt.json = true;

request(opt);


```
