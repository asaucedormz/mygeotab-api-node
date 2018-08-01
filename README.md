# mygeotab-api-node #

Unofficial nodejs client for the MyGeotab API with support for authentication with SessionId

### Getting Started ###

```
$ npm install mygeotab-api-node --save
```

### Usage ###
```
var api = new API(userName, password, database);

api.authenticate(function(err, data) {

  if(err){
    console.log('Error', err);
    return;
  }

  api.call('Get', {
    typeName: 'User',
    search: {
      name: data.userName
    }
  }, function(err, data) {

    if(err){
      console.log('Error', err);
      return;
    }

    console.log('User', data);

  });

});

//--------------------------------------------------------------------------------------------------
//---------------------------------OR---------------------------------------------------------------



let idServer = 0;

let userName= 'user_name';
let sessionId='17082007803898348770';
let database = 'database_name';
let server = `my${idServer}.geotab.com`;

let api = new API(userName, null, sessionId, database, server);
api.call('Get', {
  typeName: 'Device',
  //   search: {
  //     name: data.userName
  //   }
}, function (err, data) {

  if (err) {
    console.log('Error', err);
    return;
  }

   

console.log('User', data);

});


printAllGroups();

const printAllGroups = async()=>{
      let groups =  await api.callAsync('Get', {
          typeName: 'Group'
      });
      
      console.log(groups);  
}

```

### Running Tests ###
```
$ npm install -g mocha
$ npm install
$ mocha
```
