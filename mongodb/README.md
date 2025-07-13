# MongoDB

## mongosh

```sh
# Always start with
mongosh
# Connect to database
use myDatabase
```

### Insert

```shell
# Insert a single document
# db.<collection>.insertOne(<document>
db.users.insertOne({
  name: "John Doe",
  email: "john@example.com",
  age: 30,
  city: "New York",
  createdAt: new Date()
})
```

### Delete

```shell
# Delete a single document
# db.<collection>.deleteOne(<document>
db.data.deleteOne(
  {"_id": ObjectId("686897be9f8f3f887ee1e765")}
)
```

### Duplicate a collection

```shell
# Duplicate a collection
# db.<originalCollection>.aggregate([
#   { $out: "<newCollectionName>" }
# ])
db.originalCollection.aggregate([
  { $out: "newCollectionName" }
])
```

### Update

```shell
# Update file

# Add a field into existing entree in a collection
# db.<collection>.updateOne(
#   { _id: ObjectId("<your_document_id>") 
#   { $set: { <arrayField>: "<newElement>" } }
# )
db.collection.updateOne(
  { _id: ObjectId("686897be9f8f3f887ee1e765") },
  { $set: { arrayField: "newElement" } }
)

# Adding/Update a Property to an Embedded Object
# db.<collection>.updateOne(
#   { _id: ObjectId("<your_document_id>") },
# {
#   $set: {
#     "currencyExchange.USD": {
#       exgAmount : 150
#     }
#   }
# }
# )
db.collection.updateOne(
  { _id: ObjectId("686897be9f8f3f887ee1e765") },
  { 
    $set: { 
      "currencyExchange.USD": {
        exgCurrencyRate: "1.0",
        exgCurrencyBaseAmount: 100,
        exgCurrencyAdditionAmount: 50,
        exgCurrencyTotal: 150
      }
    }
  }
)
```