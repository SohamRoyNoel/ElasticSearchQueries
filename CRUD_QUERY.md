GET /_cluster/health

GET /_cat/nodes

GET /_cat/indices

PUT /products
{
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 1
  }
}

POST /products/_doc
{
  "name": "alu bom",
  "price": 200,
  "inStock": 300
}

PUT /products/_doc/100
{
  "name": "potol bom",
  "price": 69,
  "inStock": 10
}

GET /products/_doc/100

POST /products/_update/100
{
  "doc": {
    "inStock": 9
  }
}

POST /products/_update/100
{
  "doc": {
    "tax": 900,
    "tags": ["bomb", "ganja bomb"]
  }
}

POST /products/_update/100
{
  "doc": {
    "tags": 78
  }
}

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.inStock--"
  }
}

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.inStock = 10"
  }
}

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.inStock -= params.quantity",
    "params": {
      "quantity": 2
    }
  }
}

POST /products/_update/100
{
  "script": {
    "source": """
        if(ctx._source.inStock > 0) {
          ctx._source.inStock--
        }
      """,
    "params": {
      "quantity": 4
    }
  }
}



