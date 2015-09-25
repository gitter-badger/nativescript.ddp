#Nativescript DDP Client

[![Join the chat at https://gitter.im/emmanuelbuah/nativescript.ddp](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/emmanuelbuah/nativescript.ddp?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This is cross plaform DDP Client for Nativescript 


## Installation 

Run 'tns plugin add [npm, folder, git repo src]

## Proposed Api/Usage
```
//Connection
var Meteor = MeteorConnect("localhost:3000");
Meteor.disconnect();
Meteor.reconnect();


//Accounts/Authentication
Meteor.loginWithPassword(function(error,result){
	//callback after authentication
});
Meteor.loginWithFacebook(function(error,result){
	//callback after authentication
});
Meteor.loginWithTwitter(function(error,result){
	//callback after authentication
});

Meteor.logout(function(error,result){
	//callback after logout
	//similar to http://docs.meteor.com/#/full/meteor_logout
});

Meteor.createUser(options, function(error,result){
	//callback after use creation
	//options= { username:w, email:x, password: y, profile: z}
	//similar to http://docs.meteor.com/#/full/accounts_createuser
})

//Auth user access
var user = Meteor.user;

//Subscription
var taskSubscription = Meteor.subscribe("v1/tasks");
taskSubscription.on('stop',function(){
	//callback when subscription is stopped
});
taskSubscription.on('ready',function(){
 	//callback when subscription is ready
});
taskSubscription.stop(); //Stop subscription
taskSubscription.ready(); //True or False

//Method call
Meteor.call("v1/task/new",function(error,result){
  //code here
});

//Collection
var Tasks = Meteor.Collection("tasks", {
  transform: function (doc) { doc.status=0; return doc; }
});

//Insert
var task = Tasks.insert({ description: "Buy Milk" });
//Updaet
Tasks.update({ description: "Buy Milk" }},
                   {done: true},
                   {multi: fale});
});
//Delete
Tasks.remove({description: "Buy Milk"});
//Find
var task = Tasks.FindOne({ done: true });
var taskquery = Tasks.Find({ done: true });
var result = taskquery.fetch();

//live query
taskquery.on('added'/*'changed','removed'*/,function(id, doc){
   //do something here
});


 

```

## Discussion (Gitter - N/A) 
- Thoughts on Api
- Identify disparate technology (nativescript observable, minimongo, websocket, facebook, twitter) intersection/integration point 
- Identify first set of api to implement
- Implementation direction: Refactor meteor client code for nativescript (similar to https://github.com/aleclarson/meteor-client/wiki/Available-Packages) or implement from scratch. 




