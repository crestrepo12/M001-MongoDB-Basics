# Chapter 2
## Introduction to CRUD
* Create
* Read
* Update
* Delete

## Mongo Shell - using OSX

## Loading Data into Your Sandbox Cluster

## How to connect Atlas Sandbox Cluster from Compass

## Creating Documents: Insert One
1. Inserting through Compass:


2. Inserting through Mongo Shell : *insertOne()*
	* Network Error-
		* Left the shell inactive, it had terminated the connection but when making it connection, it will reconnect
	 * Example: Make sure your in the correct Database to insert data to the correct Collection.
> 	```db.moviesScratch.insertOne({title:"Star Trek II: The Wrath of Khan", year: 1982, imdb: "tt0084726"})```

Mongo will generate an `_id`  automatically, 
`_id`  values created for us by MongoDB are of type ObjectId not int32. The rest of the statements are true and either mentioned or illustrated in the preceding lesson video.

But you can manually insert an `_id` yourself by simply adding the field with id your choice (below) :

> `db.moviesScratch.insertOne({_id: "tt0084726", title: "Star Trek II: The Wrath of Khan", year: 1982, imdb: "tt0084726"})`


## Creating Documents: Insert Many
* for an **_ordered insert_**: 

Below: the first two objects pass the condition but at the third object, the condition does not pass and therefore does not insert the rest of the data in the array that does pass.

```
db.moviesScratch.insertMany(
    [
        {
  	    "_id" : "tt0084726",
  	    "title" : "Star Trek II: The Wrath of Khan",
  	    "year" : 1982,
  	    "type" : "movie"
          },
          {
  	    "_id" : "tt0796366",
  	    "title" : "Star Trek",
  	    "year" : 2009,
  	    "type" : "movie"
          },
          {
  	    "_id" : "tt0084726",
  	    "title" : "Star Trek II: The Wrath of Khan",
  	    "year" : 1982,
  	    "type" : "movie"
          },
          {
  	    "_id" : "tt1408101",
  	    "title" : "Star Trek Into Darkness",
  	    "year" : 2013,
  	    "type" : "movie"
          },
          {
  	    "_id" : "tt0117731",
  	    "title" : "Star Trek: First Contact",
  	    "year" : 1996,
  	    "type" : "movie"
        }
    ]
)
```


* for **_unordered insert_**: 
	* ::NOTE:: there is ordered property that tells that simply states that it is not ordered ( `ordered: false`) so that it can continue through the whole list and not stop inserting the data
```
db.moviesScratch.insertMany(
    [
        {
	    "_id" : "tt0084726",
	    "title" : "Star Trek II: The Wrath of Khan",
	    "year" : 1982,
	    "type" : "movie"
        },
        {
	    "_id" : "tt0796366",
	    "title" : "Star Trek",
	    "year" : 2009,
	    "type" : "movie"
        },
        {
	    "_id" : "tt0084726",
	    "title" : "Star Trek II: The Wrath of Khan",
	    "year" : 1982,
	    "type" : "movie"
        },
        {
	    "_id" : "tt1408101",
	    "title" : "Star Trek Into Darkness",
	    "year" : 2013,
	    "type" : "movie"
        },
        {
	    "_id" : "tt0117731",
	    "title" : "Star Trek: First Contact",
	    "year" : 1996,
	    "type" : "movie"
        }
    ],
    {
        "ordered": false 
    }
) 
```