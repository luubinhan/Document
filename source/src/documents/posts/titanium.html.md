# persist and load a Singleton model

File xml

<Model id="userInfo"/>

Then you can access it in any controller as Alloy.Models.userInfo

var userInfo = Alloy.Models.userInfo;
 
// fetch() the stored model from sqlite persistence
userInfo.fetch();
 
// Change the "cookie" in the client-side model
userInfo.set('cookie', 'SOME_COOKIE_STRING');
 
// Persist the state of the client-side model to the server-side storage. In
// this case, "server-side" simply refers to the local sqlite database
userInfo.save();
 
// You can also do this in one step
userInfo.save({
    cookie: 'SOME_COOKIE_STRING'