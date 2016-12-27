# PaaS Catalog service

### PaaS Catalog service will provide the list of services that are available in Foundry along with the platforms where they are deployed. It will also pull the list of services that are available in the target platform. The metadata of all the services and its supporting platforms will be stored in gist/db(mongo/postgre). The user will be able to see the list of services and search for a service.

## PaaSCatalog Service API

## POST /PaaSCatalog/catalog?type=typeofrequireddata
- This API will provide the data based on the type.

### Request

| Query Params  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| type  | type of the required data. ex: category/hooks/services...    |

### Response


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | will return body data based on type.                                                                                          ex:{"Description":"Add the list of processors from the below.","Processor":[{"name":"Filter","id":"5a34e8ca1e3b438abaac3238fb4abc38","description":"Use the filter to create your custom filters to filter the data before being sent to the datalake.","issupported":true},{"name":"Transform","id":"423ebbe081b64d8ab23577256a539cd8","description":"Use the transform to create your custom expression for transforming the data that is sent to the datalake.","issupported":true},{"name":"Scriptable Transform","id":"619eb81935d44453a87f1fb943db86ee","description":"Use scriptable transform to provide your custom javascript that can transform the data before storing on to the datalake.","issupported":true}]}  |


- After all configuration is done, start the application and try 'YOUR_DOMAIN_URL' or 'YOUR_DOMAIN_URL'/catalog in the browser. For eg: http://localhost:3000/catalog or http://localhost:3000/
