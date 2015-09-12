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

## output

```
$httpBackend.when('GET','https://dre.540.co:443/api/searches?limit=5').respond({"meta":{"limit":5,"offset":0,"total_count":103,"execution_time":"0.002s"},"data":[{"search":"motrin","count":71},{"search":"advil","count":49},{"search":"ibuprofen","count":36},{"search":"tylenol","count":21},{"search":"enbrel","count":16}]})

$httpBackend.when('GET','https://dre.540.co:443/api/reactions?limit=5').respond({"meta":{"limit":5,"offset":0,"total_count":3507,"execution_time":"0.007s"},"data":[{"reaction":"anxiety","definitions":[{"votes":{"ups":0,"downs":0},"definition":"a painful or apprehensive uneasiness of mind usually over an impending or anticipated ill","source":"dictionaryapi.com","created_at":1436181515461},{"votes":{"ups":0,"downs":0},"definition":"an abnormal and overwhelming sense of apprehension and fear often marked by physiological signs (as sweating, tension, and increased pulse), by doubt concerning the reality and nature of the threat, and by self-doubt about one's capacity to cope with it","source":"dictionaryapi.com","created_at":1436181515462},{"votes":{"ups":0,"downs":0},"definition":"A state of uneasiness and apprehension, as about future uncertainties.","source":"wordnik.com","created_at":1436181515650},{"votes":{"ups":0,"downs":0},"definition":"A cause of anxiety:  For some people, air travel is a real anxiety. ","source":"wordnik.com","created_at":1436181515650},{"votes":{"ups":0,"downs":0},"definition":"Psychiatry   A state of apprehension, uncertainty, and fear resulting from the anticipation of a realistic or fantasized threatening event or situation, often impairing physical and psychological functioning.","source":"wordnik.com","created_at":1436181515650},{"votes":{"ups":0,"downs":0},"definition":"Eager, often agitated desire:  my anxiety to make a good impression. ","source":"wordnik.com","created_at":1436181515650}],"last_updated":1436181515650},{"reaction":"intra-uterine contraceptive device expelled","definitions":[],"last_updated":1436285624924},{"reaction":"pain","definitions":[{"votes":{"ups":2,"downs":1},"definition":"An unpleasant sensation occurring in varying degrees of severity as a consequence of injury, disease, or emotional disorder.","source":"wordnik.com","created_at":1436181515660},{"votes":{"ups":0,"downs":0},"definition":"Suffering or distress.","source":"wordnik.com","created_at":1436181515660},{"votes":{"ups":0,"downs":0},"definition":"The pangs of childbirth.","source":"wordnik.com","created_at":1436181515660},{"votes":{"ups":0,"downs":0},"definition":"Great care or effort:  take pains with one's work. ","source":"wordnik.com","created_at":1436181515660},{"votes":{"ups":0,"downs":0},"definition":"Informal   A source of annoyance; a nuisance.","source":"wordnik.com","created_at":1436181515660}],"last_updated":1437656292702},{"reaction":"vomiting","definitions":[{"votes":{"ups":0,"downs":0},"definition":"an act or instance of disgorging the contents of the stomach through the mouth ","source":"dictionaryapi.com","created_at":1436181515472},{"votes":{"ups":0,"downs":0},"definition":"The action of the verb vomit","source":"wordnik.com","created_at":1436181515663}],"last_updated":1436181515663},{"reaction":"nausea","definitions":[{"votes":{"ups":2,"downs":1},"definition":"a stomach distress with distaste for food and an urge to vomit","source":"dictionaryapi.com","created_at":1436181515455},{"votes":{"ups":13,"downs":0},"definition":"A feeling of sickness in the stomach characterized by an urge to vomit. See Usage Note at nauseous.","source":"wordnik.com","created_at":1436181515665},{"votes":{"ups":0,"downs":0},"definition":"Strong aversion; disgust.","source":"wordnik.com","created_at":1436181515665}],"last_updated":1441217818838}]})


```
