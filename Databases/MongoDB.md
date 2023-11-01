--------------------------------------------------------------------------------
MongoDB - Notes
--------------------------------------------------------------------------------
Basic commands               |
  Enter Shell interface      | mongosh
                             |
  Show Collections           | show collections
                             |
  Show availabe Databases    | show dbs
                             |
  Connect and use a Database | use <database name>
    (work within a context)  |
                             |
--------------------------------------------------------------------------------
Frequent query lang commands |
  * **find and select docs**     | find()
    example                  |   db.cars.find()             - outputs all cars
                             |   db.cars.find({year:2019})  - outputs with defined context
      **Filter Conditions**      |   `db.cars.find({year:{'$gt':2015},price:{$lt:7000},brand:'Ford'}).pretty`
                             |
                             |
    find **Projections**         | Projections allow the limiting and setting of
                             | of the fields that will be returned from the query
                             | results. A Projection is just a JSON object in 
                             | which the keys are the name of the fields, while
                             | the values are 0 if we want to exclude a fild from 
                             | the output, or 1 if we want to include it
      example                |   db.<tableName>.find({searchCondition: 'value'},{ProjectionField01:1,ProjectionField02:0})
                             |   `db.cares.find({brand:'Ford',make:'Fiesta'},{year:1,km:1,_id:0})`
                             |
    Sort returned results    | db.collections.find()**.sort({sortParamter:1})**
                             |
    Limit the number of      | db.collections.find()**.limit(5)**
    returned results         |
                             |
    (Sort and limit can be   | db.collections.find().sort().limit()
     daisy chained)          |
                             |
  * **Create a new document**    | insertOne()
  * **Create an array of do**cs  | insertMany()
  * **Update one or mod doc**s   | updateOne(), updateMany()
  * **Delete documents**         | deleteOne(), deleteMany()
                             |
                             |
                             |
                             |
                             |
                             |
