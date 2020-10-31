# MongoDBWrapper-Notes-for-Zero

### How to use MongoDBEconomy Wrapper
Step 1: add the module to the top of the index file, like so: `const MongoDBWrapper = require('./src/module/MongoDBEconomy');`  

Step 2: add `MongoDBWrapper.connectDatabase("mongodb+srv://<UserName>:<Password>@cluster0.lvsr3.mongodb.net/<databaseName>?retryWrites=true&w=majority");` to your 
```js
client.on('ready', () => {
    // add here
});
```
And change <UserName>, <Password> and <databaseName> to their correct values  

you can use: `MongoDBWrapper.pair(<var1>, <var2>);` to pair two things together and `MongoDBWrapper.unpair(<var1>, <var2>);` to unpair two things from each other  
Worked Example:
```js
let firstMember = args[0];
let secondMember = args[1];
// pairing
MongoDBWrapper.pair(firstMember, secondMember);

// unpairing
MongoDBWrapper.unpair(firstMember, secondMember);
```
\
Finally: in the disconnect section of your code (if you have one) place `MongoDBWrapper.disconnect()` into the event watcher  
Worked Example:
```js
client.on("disconnect", () => {
    process.exit(0); // close the program on a disconnect (use PM2 or a hosting service to auto-restart)
    MongoDBWrapper.disconnect(); // disconnect from database
});
```
