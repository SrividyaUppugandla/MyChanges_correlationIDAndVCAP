# PaaS Catalog service

#### PaaS Catalog service will provide the list of services that are available in Foundry along with the platforms where they are deployed. It will also pull the list of services that are available in the target platform. The metadata of all the services and its supporting platforms will be stored in gist/db(mongo/postgre). The user will be able to see the list of services and search for a service.

## PaaSCatalog Service API

## GET /PaaSCatalog/catalog?type=typeofrequireddata
- This API will provide the data based on the type.

### Request

| Query Params  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| type  | type of the required data. ex: category/hooks/services...    |

### Response (/PaaSCatalog/catalog?type=processorType)


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"Description":"Add the list of processors from the below.","Processor":[{"name":"Filter","id":"5a34e8ca1e3b438abaac3238fb4abc38","description":"Use the filter to create your custom filters to filter the data before being sent to the datalake.","issupported":true},{"name":"Transform","id":"423ebbe081b64d8ab23577256a539cd8","description":"Use the transform to create your custom expression for transforming the data that is sent to the datalake.","issupported":true},{"name":"Scriptable Transform","id":"619eb81935d44453a87f1fb943db86ee","description":"Use scriptable transform to provide your custom javascript that can transform the data before storing on to the datalake.","issupported":true}]}  |


## GET /PaaSCatalog/searchCatalog?searchString=stringtosearch&type=typeofrequireddata
- This API will provide the services data based on the searchString.

### Request

| Query Params  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| searchString  | string to search.    |
| type  | type of the required data. ex: category/hooks/services...    |

### Response (/PaaSCatalog/searchCatalog?searchString=oauth&type=category) 


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"result":[{"headers":[{"id":"735af8859bc840188dbc0f7974f91bf6","text":"OFFERINGS"},{"id":"7793bf2e279c4f21acc3723512b5f8ad","text":"SETTINGS"},{"id":"1c835c73bd1e4407b4d30c29ef5c9859","text":"AUTH HOOKS"},{"id":"f6e519d0471b4f7687d6a4d281d655d3","text":"LOGGERS"}],"keys":["facebook","google","linkedin","twitter","authentication","oauth","openid","saml"],"name":"Authentication","description":"The Authentication microservice enables you to set up authentication function feature in your web or mobile app very quickly. Use protocols or providers of your choice and configure pre- and post auth hooks to add additional layer of security. You can also have the authentication microservice bound with a sample application code, customize the app in accordance to your business needs and push the app into a selected PaaS platform.","id":"d766af26-54a5-4d7e-b64b-e5ece3d02150","starterKitID":["1002"],"loggerid":"f271f751-37e7-45df-a47c-d20b9dde4f96","appUrl":"NodeJS/Authentication","isNative":true,"platforms":[2004,2001,2002,2003]}]}  |


## GET /PaaSCatalog/platformservices?id=id&platform=platform&regionID=regionid
- This API will provide the services data based on the id, platform, regionID. Platform is either foundry/blumix/pivotal/azure. If platform is either blumix/pivotal/azure, services data will return along with foundry service information.

### Request

| Query Params  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| id  | service unique ID    |
| platform  | ID of platform. ex: 2004/2001    |
| regionID  | ID of region(which region service details)    |

### Response (/PaaSCatalog/platformservices?id=d766af26-54a5-4d7e-b64b-e5ece3d02150&platform=2002&regionID=f4cf84f1edf94379a2ea2302bac3cd13) 


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | [{"name":"Authentication","description":"The Authentication microservice enables you to set up authentication function feature in your web or mobile app very quickly. Use protocols or providers of your choice and configure pre- and post auth hooks to add additional layer of security. You can also have the authentication microservice bound with a sample application code, customize the app in accordance to your business needs and push the app into a selected PaaS platform.","id":"d766af26-54a5-4d7e-b64b-e5ece3d02150","isNative":true,"platforms":[2004,2001,2002]},{"id":"d766af26-54a5-4d7e-b64b-e5ece3d02150","guid":"a90c6af0-2ed0-4b43-8cb6-9f6c908aef3c","url":"/v2/services/a90c6af0-2ed0-4b43-8cb6-9f6c908aef3c","redirectUrl":"https://console.ng.bluemix.net","created_at":"2014-12-23T02:56:49Z","updated_at":"2016-05-04T22:04:30Z","description":"Implement user authentication for your web and mobile apps quickly, using simple policy-based configurations.","name":"SingleSignOn","isNative":false,"regions":{"f4cf84f1edf94379a2ea2302bac3cd13":{"authorization_endpoint":"https://login.ng.bluemix.net"},"72b4fb87bb3941ca93fa9765fed7a010":{"authorization_endpoint":"https://login.eu-gb.bluemix.net"},"fab747df40d941f28bb219042a27c395":{"authorization_endpoint":"https://login.au-syd.bluemix.net"}},"platforms":[2002],"authorization_endpoint":"https://login.ng.bluemix.net"}]  |


## GET /PaaSCatalog/regions?platformID=platformID
- This API will provide the regions available for the particular platform

### Request

| Query Params  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| platform  | ID of platform. ex: 2004/2001    |

### Response (/PaaSCatalog/regions?platformID=2004) 


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"regions":[{"id":"b3cf793fc9da4754bcdd0386b2d34177","name":"Default","api_url":"https://api.qa.cognizantone.org","login_url":"https://login.qa.cognizantone.org/oauth/token","host":"qa.cognizantone.org"},{"id":"3812805e5f7b11e68b7786f30ca893d3","name":"Dev","api_url":"https://api.cognizantone.org","login_url":"https://login.cognizantone.org/oauth/token","host":"cognizantone.org"},{"id":"2fafe8387fd847b4868e4b96f44912f8","name":"Global","api_url":"https://api.mvp2.cognizantone.org","login_url":"https://login.mvp2.cognizantone.org/oauth/token","host":"mvp2.cognizantone.org"}]}  |


## GET /PaaSCatalog/organizations
- This API will provide the organizations available in provided api

### Request

| Headers  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| Authorization  | token to authorize to domain    |
| api_url  | api url ex: http://api.mvp2.cognizantone.org    |

### Response


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | list of organizations available in domain  |


## GET /PaaSCatalog/spaces
- This API will provide the spaces of organization for the provided api

### Request

| Headers  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| Authorization  | token to authorize to domain    |
| api_url  | api url ex: http://api.mvp2.cognizantone.org    |
| orgguid  | id of organization. which can get from above api    |

### Response


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | list of spaces for the organization.  |


## GET /PaaSCatalog/appNameCheck
- This API will check for the existence of app based on appname provided in the provided domain

### Request

| Headers  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| Authorization  | token to authorize to domain    |
| api_url  | api url ex: http://api.mvp2.cognizantone.org    |
| spaceguid  | id of space. which can get from above api    |
| appname  | name of the app to check    |

### Response (If appname exists)


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"Error":"App name is already taken"}  |

### Response (If appname doesn't exist)


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"Success":"Success"}  |


## GET /PaaSCatalog/platform
- This API will provide the list of platforms

### Response


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"platforms":[{"id":"2004","name":" Foundry"},{"id":"2001","name":"Pivotal"},{"id":"2002","name":"IBM Bluemix"},{"id":"2003","name":"Microsoft Azure"}]}  |


## GET /PaaSCatalog/getExistingInstances
- This API will get the existing instance of service.

### Request

| Headers  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| Authorization  | token to authorize to domain    |
| api_url  | api url ex: http://api.mvp2.cognizantone.org    |
| spaceguid  | id of space. which can get from above api    |
| platformID  | Id of platform   |
| regionID  | Id of region   |
| categoryName  | name of service for which existing instances are needed   |
| spacename  | space name   |

### Response


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"ExistingInstances":[{"guid":"908af5ab-92b5-468d-aa08-7e065ac98a32","name":"dffgmongodb"},{"guid":"8f32874c-2435-46c2-aa8f-a94b90d1f0a6","name":"PushMongo"}],"Plans":[{"guid":"87acfb26-de03-4b26-a122-b3823218c4ee","name":"Sandbox"},{"guid":"1683886c-555c-4bb3-91c6-504f7793e3b5","name":"Dedicated Single-Node"},{"guid":"3d87d632-8060-4237-bf13-c777bffaeced","name":"Shared Cluster"},{"guid":"b1dd543c-36e4-4b7b-9bae-4f21001fd1b7","name":"Dedicated Cluster"}]}  |


## GET /PaaSCatalog/getdomainserviceplanguid
- This API will get the plan guid of service.

### Request

| Headers  |                  Description                                                          |
|--------------|---------------------------------------------------------------------------------------|
| Authorization  | token to authorize to domain    |
| api_url  | api url ex: http://api.mvp2.cognizantone.org    |
| spaceguid  | id of space. which can get from above api    |
| platformID  | Id of platform   |
| regionID  | Id of region   |
| categoryName  | name of service for which existing instances are needed   |
| spacename  | space name   |

### Response


| HTTP           |Value|
|----------------|--------------------------------------|
|   status code |200 |
|body   | {"result":[{"guid":"b653f759-d04c-45ee-bb79-a0fdf7ba2a30","name":"free"}]}  |


- After all configuration is done, start the application and try 'YOUR_DOMAIN_URL' or 'YOUR_DOMAIN_URL'/catalog in the browser. For eg: http://localhost:3000/catalog or http://localhost:3000/
