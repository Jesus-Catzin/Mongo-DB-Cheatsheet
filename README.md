# Mongo-DB-Cheatsheet

The porpuse of this is to make easier and shor the way to learn to use MongoDB in the same while I learning!
If there are any question or error let me know! 

## What is MongoDB?

MongoDB is a general-purpose, document-based, distributed database that has been designed for modern application developers and the cloud era.

What does this mean is that MongoDB is a NoSQL Database that make faster and eficienty compared with the traditional SQL.

### Install MongoDB.

To beging with, first at all you need to install MongoDB [click here](https://www.mongodb.com/download-center/community) to install for your own operative system.

Because I'm using windows, I need to add to the path enviroment. [click here](https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/) to add it for any program.

## Starting with MongoDB

In my case, the database used was provided by my teacher who created it in Atlas, which is a cloud database (from Mongo DB) therefore we needed access trough a link from him to use it in the cmd.

he first thing would be opening the command window and use the link provided, in my case this will do:
```mongodb
mongo "mongodb+srv://cluster0-cdd34.mongodb.net/next" --username YourUsernamehere password writehere
```
The password element is only write if it is required.

## Commands:
```mongodb
 show dbs
```
![alt text] (https://github.com/Jesus-Catzin/Mongo-DB-Cheatsheet/blob/master/Mongo%20Pictures/1.PNG "1")

This will show you the whole databases in mongo including the ones you have created (if you have done it).

```mongodb
 use "database name"
```
This will allow you use one database or if the database doesn't exist it will automatically create it.
```mongodb
help 
```
This will show you the most important options in Mongo Shell
```mongodb
 db.getName()
```
This return the database name you are.
```mongodb
 db.dropDatabase()
```
You delete the actual database you are
```mongodb
 db.collectionname.insert({"key":"atribute"})
```
This will create or use a collection with that name, "insert" is used to insert the values like dictionaries in mongoDB where the first value is your key and the next is the atribute or values.
* It must return: WriteResult({ "nInserted" : 1 }) if the result is okay!

```mongodb
 db.collectionname.find()
```
"find" without any value inside return the whole collections' elements.

If you add some parameter you can find with specific values.

```mongodb
 db.collectionname.find({})
```

```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
```mongodb
 
```
