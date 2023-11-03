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
  * **Searching for documents**  |
    find and select docs     | find()
    example                  |   db.cars.find()             - outputs all cars
                             |   db.cars.find({year:2019})  - outputs with defined context
      **Filter Conditions**      |   `db.cars.find({year:{'$gt':2015},price:{$lt:7000},brand:'Ford'}).pretty`
                             |
      some common filter     | '$gt' (greater than), '$lt' (less than), '$inc' (increment)
      conditions             |
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
  * **Creating Documents**       |
    Create a new document    | insertOne()
    Create an array of docs  | insertMany()
    Update one or mod docs   | updateOne(), updateMany()
                             |
  * **Updating Documents**       |
    Updated first found doc  | db.collections.**updateOne()**
      example                |   db.cars.updateOne({make:'Fiesta'},**{$set:{'Salesman':'Marko'}**})
                             |
    Update Many documents    | db.collections.**updateMany**()
      example                |   db.cars.updateMany({make:'Fiesta'},{$inc:{price: -200}})
                             |
  * **Deleting documents**       |
    Delete documents         | deleteOne(), deleteMany()
                             |
  **Cursors (introduction)**     | Cursors enable us to perform some standared database
                             | Opearations on returned documents, such aslimiting the
                             | number of results, ordering by one or more keys ascending
                             | or descending, skipping records, just to name a few.
                             |
    Cursor example           | let fiesta_cars = db.cars.find({'make':'Fiesta'})
                             |
                             | This query returns the 5 least expensive cars made in 2015
                             | `db.cars.find({years:2015},{brand:1,make:1,year:1,_id:0,price:1}).sort({price:1}).limit(5)`
                             |
  **Aggregation framework**      | The Aggregation framework is an alternative way
                             | to retrieves sets of documents from a collection, with the
                             | added benefit of the possibility of data processing
                             | in different stages or steps. With the aggregation 
                             | pipeline, basically, documents are pulled from MongoDB 
                             | collection, which then are fed sequentially to 
                             | various stages of the pipleine were each stage output
                             | is fed to the next stage's input until a final
                             | set of documents is returned
                             |
    Aggregation states       | $math    - Match only specific documents 
                             | $project - Select existing fields or derive new ones
                             | $group   - Group according to a categorical feautre
                             | $sort    - Sort in ascending or descending order using a field
                             | $limit   - Limit the results to a predefined number
                             |
    Aggregation examples     | * An aggregation which mimics the .find() command
                             |   db.cars.aggregate([{$match: {braind:"Fiat"}}])
                             |
                             |  db.collections.aggregate({
                             |    {$match:{brand:"Fiet"}},            <- matching clause
                             |    ## id is mandatory| $make = Filed used for grouping
                             |    ## avgPrice = the name of the quantity (arbitrary)
                             |    ## $avg = **Aggregation function**
                             |    ## $price = the field used for performing the aggregation
                             |    `{$group:{_id:{model:"$make"},avgPrice:{$avg:"$price"}}}`
                             |
                             |   db.cars.aggregate([
                             |     {$match: {brand:"Fiat"}},
                             |     `{$group:{_id:{model:"$make"},avgPrice: { $avg: "$price" } }}`
                             |   ])
                             |
    **Project operator**         | Pipelines can also include data processing through
                             | the project operator - a handy tool for creating
                             | entierly new fields, derived from existing document
                             | fileds, that are then carried into the nex stages
                             |
      Aggregation with       | db.cars.aggregate([
      Project operator       |   {$match: {brand:"Opel"}},
                             |   {**$project**:{`_id:0,price:1,year:1,fullName:`
                             |     `{$concat:["$make", " ", "$brand"]}}},`
                             |   {$group:{
                             |     `_id:{make:"$fullName"},avgPrice:{$avg:"$price"}}},`
                             |   {$sort: {avgPrice: -1}},
                             |   {$limit: 10}
                             | ]).pretty()
