# Deploying an Express Application

Intro

## The Express Application explained

### Get the App

clone info
~~~
$ git clone `remote`
$ cd dir_name
~~~

### Dependency Tracking

npm Ado. `package.info` contents:
~~~
{
  "name": "ExpressTut",
  "version": "0.0.1",
  "private": true,
  "scripts": {
    "start": "node app"
  },
  "dependencies": {
    "express": "3.4.0",
    "jade": "*",
    "mongodb": "1.3.19"
  }
}
~~~

### Process Type Definition

Procfile:
~~~
web: node app.js
~~~

### Database

Mongodb, `employeeprovider.js` content:
~~~
var Db = require('mongodb').Db,
    MongoClient = require('mongodb').MongoClient,
    Server = require('mongodb').Server,
    ReplSetServers = require('mongodb').ReplSetServers,
    ObjectID = require('mongodb').ObjectID,
    Binary = require('mongodb').Binary,
    GridStore = require('mongodb').GridStore,
    Grid = require('mongodb').Grid,
    Code = require('mongodb').Code,
    BSON = require('mongodb').pure().BSON,
    assert = require('assert');

EmployeeProvider = function() {
  var that = this;
    MongoClient.connect(process.env.MONGOLAB_URI, function(err, db){
    if(err) { return console.dir(err); }
    that.db = db;
  })
};
...
~~~

## Pushing and Deploying your App

ado

~~~
$ cctrlapp APP_NAME create nodejs
~~~

~~~
$ cctrlapp APP_NAME/default push
push output
...

~~~

Add mongolab
~~~
$ cctrlapp APP_NAME/default addon.add mongolab.free
$ cctrlapp APP_NAME/default deploy
~~~

Congrats

Links + References
