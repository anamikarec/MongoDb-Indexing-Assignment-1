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
