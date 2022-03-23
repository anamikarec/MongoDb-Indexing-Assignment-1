# MongoDb-Indexing-Assignment-1

### Part:~1

#### use the airbnb listing collection
#### index the price field
#### note down the time difference between the queries.
#### try queries where you check for a range of values ( gte, lte, in etc )
#### do an index on a nested sub document (like location etc) and do queries on that as well
#### do queries on two indexes and see when rejected plans happen


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
```js
        db.listing.createIndex({"price":1});
```
