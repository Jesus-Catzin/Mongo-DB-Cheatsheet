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
This will show you the whole databases in mongo including the ones you have created (if you have done it).
```mongodb
 show dbs
```
Output:
```mongodb
<jack>               0.000GB
AndysToys            0.000GB
GM_test              0.000GB
Jeorval_test         0.000GB
Sam                  0.000GB
Sami_DB              0.000GB
admin                0.000GB
alexa_test           0.000GB
brenda_test          0.000GB
collectionTest       0.000GB
erosa_greek          0.000GB
fatima               0.000GB
gonzalo              0.000GB
isaac                0.000GB
local               12.293GB
menu_restaurant      0.000GB
newLis               0.000GB
nuevabd              0.000GB
pabloe_duarte        0.000GB
products             0.000GB
sample_F             0.000GB
sample_airbnb        0.051GB
sample_analytics     0.009GB
sample_geospatial    0.001GB
sample_mflix         0.042GB
sample_supplies      0.001GB
sample_training      0.059GB
sample_weatherdata   0.002GB
test                 0.002GB
test_potions         0.000GB
usuarios             0.000GB
```
This will allow you use one database or if the database doesn't exist it will automatically create it.
In this case we will use "sample_airbnb" to work with.
```mongodb
 use "sample_airbnb"
```
```
switched to db sample_airbnb
```
This will show you the most important options in Mongo Shell
```mongodb
help 
```
Output:
```mongobd
  db.help()                    help on db methods
        db.mycoll.help()             help on collection methods
        sh.help()                    sharding helpers
        rs.help()                    replica set helpers
        help admin                   administrative help
        help connect                 connecting to a db help
        help keys                    key shortcuts
        help misc                    misc things to know
        help mr                      mapreduce

        show dbs                     show database names
        show collections             show collections in current database
        show users                   show users in current database
        show profile                 show most recent system.profile entries with time >= 1ms
        show logs                    show the accessible logger names
        show log [name]              prints out the last segment of log in memory, 'global' is default
        use <db_name>                set current database
        db.foo.find()                list objects in collection foo
        db.foo.find( { a : 1 } )     list objects in foo where a == 1
        it                           result of the last line evaluated; use to further iterate
        DBQuery.shellBatchSize = x   set default number of items to display on shell
```
This return the database name you are.
```mongodb
 db.getName()
```
```mongodb
sample_airbnb
``` 
You delete the actual database you are
```mongodb
 db.dropDatabase()
```


This will create or use a collection with that name, "insert" is used to insert the values like dictionaries in mongoDB where the first value is your key and the next is the atribute or values.
```mongodb
 db.collectionname.insert({"key":"atribute"})
```

* It must return: WriteResult({ "nInserted" : 1 }) if the result is okay!
## Starting With Queries
"find" without any value inside return the whole collections' elements.
```mongodb
 db.listingsAndReviews.find()
```
In this case I won't run it because it's too long. 

```mongodb
 db.listingAndReviews.find({ "name": "Ribeira Charming Duplex"})
```
In this case I won't run it because it's too long, but with this specifications it will find the documents that matches it!
If you add some parameter you can find with specific values.


This will delete the document(s) that will match with the provided query. 
```mongodb
 db.catzin.remove({"nombre":"El Espantapajaros"})
```

This will delete the whole documents in the collection
```mongodb
 db.catzin.remove({})
```
using update the "$set" must be in order to update the record. If it doesn't you will delete all the data in that document.
```mongodb
 db.collectionname.update({"key":"value"}, {"$set":{"key":"value_to_update"}})
```
Adding the {"multi":true} will uptade the whole documents matched
```mongodb
  db.collectionname.update({"key":"value"}, {"$set":{"key":"value_to_update"},{"multi":true}})
```

In this case "update" is necesary to modify it, the parameter "$inc" is a required in order to work. This will increase/decrease each time when the user does click in a field.
```mongodb
 db.collectionname.update({"key":"value"},{"$inc":{"count":1}})
```

Adding "upsert":true, will update de document, but if that document doesn't exist, it will create it automatically.
```mongodb
 db.collectionname.update({"key":"value"},{"$inc":{"count":1}}, {"upsert":true})
```
the element "{}" is query the whole document, using the "$unset" if used to delete one element, if you add "multi":true, you will modify all the documents that matches it. 
```mongodb
db.collectionname.update({},{"$unset":{"key":""}}, {"multi":true}) 
```

Using "$rename" we can change the name of one field  (key) in our collections, {"multi":true} it's optional, if you add it you will rename the whole documents that maches it. 
```mongodb
 db.catzin.update({}, {"$rename":{"autor":"director"}}, {"multi":true})
```
Before to use rename:
```mongodb
 { "_id" : ObjectId("5ec2441f1110b504b83542fd"), "nombre" : "La momia", "autor" : "Pablo", "año" : 2009, "generos" : [ "horror", "misterio", "accion", "romance", "ciencia ficcion" ], "ratings" : { "buena" : 20, "mala" : 5 } }
```
After use rename:
```mongodb
{
        "_id" : ObjectId("5ec2441f1110b504b83542fd"),
        "nombre" : "La momia",
        "año" : 2009,
        "generos" : [
                "horror",
                "misterio",
                "accion",
                "romance",
                "ciencia ficcion"
        ],
        "ratings" : {
                "buena" : 20,
                "mala" : 5
        },
        "director" : "Pablo"
}
```

We can update values in our collections using dot notation when those are in an array. The order and positions are necesary to work with this.
```mongodb
 db.catzin.update({"nombre":"La momia"}, {"$set":{"generos.0":"comedia"}})
```
After Modification:
```mongodb
 {
        "_id" : ObjectId("5ec2441f1110b504b83542fd"),
        "nombre" : "La momia",
        "año" : 2009,
        "generos" : [
                "comedia",
                "misterio",
                "accion",
                "romance",
                "ciencia ficcion"
        ],
        "ratings" : {
                "buena" : 20,
                "mala" : 5
        },
        "director" : "Pablo"
}
```
Updating without know the positions.
```mongodb
 db.catzin.update({"generos":"accion"}, {"$set":{"generos.$":"action"}})
```
Output:

```mongodb
  {
        "_id" : ObjectId("5ec2441f1110b504b83542fd"),
        "nombre" : "La momia",
        "año" : 2009,
        "generos" : [
                "comedia",
                "misterio",
                "action",
                "romance",
                "ciencia ficcion"
        ],
        "ratings" : {
                "buena" : 20,
                "mala" : 5
        },
        "director" : "Pablo"
}
```
We can also update using dot notation + the field to update.
```mongodb
 db.catzin.update({"nombre":"La momia"}, {"$set":{"ratings.buena": 25}})
```
Using "$pop" you can delete the first or last element in your array. -1 for the first element, 1 for the last. 
```mongodb
db.catzin.update({"director":"Pablo"}, {"$pop":{"generos":1}}) 
```
Use "$push" to add the element in the end of the array.
```mongodb
 db.catzin.update({"director":"Pablo"}, {"$push":{"generos":"romance"}})
```
Use "$addToSet" to do the same as push, but if there exist the element it won't be add.
```mongodb
db.catzin.update({"director":"Pablo"}, {"$addToSet":{"generos":"romance"}}) 
```
Use "$pull" if to remove any instance, careful: if the element is repited inside the array, it will delete it. 
```mongodb
db.catzin.update({"director":"Pablo"}, {"$pull":{"generos":"romance"}}) 
```
Quering by multiplies criteria. 
```mongodb
 db.catzin.find({"director":"Pablo", "ratings.mala":5})
```
We can use logical operator in our queries to look for information.
* lt = less than
* gt = greater than
* lte =less than or equal
* gte =greater than or equal
* ne = not equal to
```mongodb
 db.catzin.find({"año":{"$lt":2012}})
```
You can combine more than one:
```mongodb
db.catzin.find({"año":{"$lt":2012, "$gt":2000}}) 
```
Using ne
```mongodb
 db.catzin.find({"director":{"$ne":"Pablo"}})
```
Use "$elemMatch" to match any result where at least one match it. 
```mongodb
db.catzin.find({"año":{"$elemMatch":{"$gt":2005, "$lt":2012}}})
```

```mongodb
 
```
