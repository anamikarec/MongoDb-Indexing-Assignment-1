# MongoDb-Indexing-Assignment-1

### Part:~1

#### Ques:~(i) use the airbnb listing collection
#### Ques:~(ii) index the price field
#### Ques:~(iii) note down the time difference between the queries.
#### Ques:~(iv) try queries where you check for a range of values ( gte, lte, in etc )
#### Ques:~(v) do an index on a nested sub document (like location etc) and do queries on that as well
#### Ques:~(vi) do queries on two indexes and see when rejected plans happen

> (i)


- let ```airbnb``` is the database and ```listing``` is the collection name
- downloaded airbnb.json
- import the airbnb file to database
- index the price
```js
  use airbnb
```
```js
  show collections
```
> (ii)


```js
        db.listing.createIndex({"price":1});
```
> (iii)

- Here time difference between the query1 and query2 is significant i.e. 9ms

> (iv)

```js
    // BEFORE INDEXING
    db.airbnb.find({price : {$lte : 70}}).explain("executionStats");
    // NOTE : Here "airbnb" is a collection inside airbnb database
    // Result of this query without indexing
    // nReturned: 1068,
    // executionTimeMillis: 25,
    // totalKeysExamined: 0,
    // totalDocsExamined: 5555

    // AFTER INDEXING
    db.airbnb.find({price : {$lte : 70}}).explain("executionStats");
    // NOTE : Here "airbnb" is a collection inside airbnb database
    // Result of this query with indexing
    // executionSuccess: true,
    // nReturned: 868,
    // executionTimeMillis: 16,
    // totalKeysExamined: 1068,
    // totalDocsExamined: 1068
```


