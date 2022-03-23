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

- Here time difference between the query1 and query2 is significant i.e. (375-92)ms = 283ms

> (iv)

```js
    // BEFORE INDEXING
    db.listing.find({price : {$lte : 70}}).explain("executionStats");
    // NOTE : Here "airbnb" is a collection inside airbnb database
    // Result of this query without indexing
    // nReturned: 1476,
    // executionTimeMillis: 375,
    // totalKeysExamined: 0,
    // totalDocsExamined: 5555

    // AFTER INDEXING
    db.listing.find({price : {$lte : 70}}).explain("executionStats");
    // NOTE : Here "airbnb" is a collection inside airbnb database
    // Result of this query with indexing
    // nReturned: 1476,
    // executionTimeMillis: 92,
    // totalKeysExamined: 1476,
    // totalDocsExamined: 1476,
```

> (v)

```js
      db.listing.createIndex({"address.country_code":1});
```

> (vi)

```js
    db.listing.find({"address.country_code":"BR"}).explain("executionStats");
    // rejectedPlans: []
```

### Part:~2

#### Ques:~1 do a compound index
#### Ques:~2 explain pros and cons of compound index
#### Ques:~3 explain prefix requirements for compound index
#### Ques:~4 when does compound index not work?
#### Ques:~5 apply compound index on 3 fields that are commonly searched in airbnb, and query those fields and sort them to see explain
> 1


```js
      db.airbnb.createIndex({"price":1,"accommodates":-1});
```
