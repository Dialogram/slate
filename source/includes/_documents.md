# Documents

## Upload PDF document

```shell
curl -X POST \
  http://api.dialogram.fr:8080/api/document \
  -H 'Authorization: Bearer <your_access_token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F 'file=@C:\path\to\my_file.pdf' \
  -F name=myDocument \
  -F description=My document description \
  -F public=true
```

```javascript
var form = new FormData();
form.append("file", "C:\\Users\\path\\to\\my_file.pdf");
form.append("name", "myDocument");
form.append("description", "My document description");
form.append("public", "true");
form.append("category", "entertainment")

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://api.dialogram.fr:8080/api/document",
  "method": "POST",
  "headers": {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer <your_access_token>",
  },
  "processData": false,
  "contentType": false,
  "mimeType": "multipart/form-data",
  "data": form
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above request returns a JSON structured like this:

```json
{
    "data": [
        {
            "type": "documents",
            "id": "<document_id>",
            "name": "myDocument",
            "link": "api.dialogram.fr:8080/medias/<timestamp>-<file_name>.pdf?accessToken=<your_access_token>",
            "nbPage": 35,
            "public": false,
            "description": "My document description",
            "status": 1,
            "category": "entertainment",
            "idTranslation": null,
            "idOwner": "<owner_id>",
            "creationDate": "2019-01-30T19:31:06.424Z"
        }
    ],
    "includes": []
}
```

This endpoint upload a new PDF document to the remote server. You will need to send the data by form-data since we are dealing with documents using HTTP.

#### HTTP Request

`POST http://api.dialogram.fr:8080/api/document`

#### Query Parameters

Key naming | Content
---------- | -------
file (type: file) | Your pdf file
name (type: string) | Your document name
description (type: string) | Your document description
public (type: boolean) | Your document privacy
category (type: string) | Your document category (health, finance, administrative entertainment, business)

<aside class="success">
Remember — a happy user is an authenticated user by token!
</aside>

## Get document by category

```shell
curl -X GET \
  http://api.dialogram.fr:8080/api/document/category/:category \
  -H 'Authorization: Bearer <your_access_token>' \
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://api.dialogram.fr:8080/api/document/catergory/:category",
  "method": "GET",
  "headers": {
    "Authorization": "Bearer <your_access_token>",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above request returns a JSON structured like this:

```json
{
    "data": [
        {
            "type": "documents",
            "id": "<document_id>",
            "name": "myDocument",
            "link": "api.dialogram.fr:8080/medias/<timestamp>-<file_name>.pdf?accessToken=<your_access_token>",
            "usageName": "<timestamp>-<file_name>.pdf",
            "nbPage": 35,
            "public": false,
            "description": "My document description",
            "status": 1,
            "category": "entertainment",
            "idTranslation": null,
            "idOwner": "<owner_id>",
            "creationDate": "2019-01-30T19:31:06.424Z"
        }
    ],
    "includes": []
}
```

This endpoint get a previously created PDF document from the remote server. You only need to be authenticated and to specify the category on the URL parameter.

#### HTTP Request

`GET http://api.dialogram.fr:8080/api/document/category/:category`

#### Query Parameters

NONE

#### Categories
-Administrative
-Business
-Entertainment
-Finance
-Health


## Get PDF document

```shell
curl -X GET \
  http://api.dialogram.fr:8080/api/document/:idDocument \
  -H 'Authorization: Bearer <your_access_token>' \
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://api.dialogram.fr:8080/api/document/:idDocument",
  "method": "GET",
  "headers": {
    "Authorization": "Bearer <your_access_token>",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above request returns a JSON structured like this:

```json
{
    "data": [
        {
            "type": "documents",
            "id": "<document_id>",
            "name": "myDocument",
            "link": "api.dialogram.fr:8080/medias/<timestamp>-<file_name>.pdf?accessToken=<your_access_token>",
            "usageName": "<timestamp>-<file_name>.pdf",
            "nbPage": 35,
            "public": false,
            "description": "My document description",
            "status": 1,
            "category": "entertainment",
            "idTranslation": null,
            "idOwner": "<owner_id>",
            "creationDate": "2019-01-30T19:31:06.424Z"
        }
    ],
    "includes": []
}
```

This endpoint get a previously created PDF document from the remote server. You only need to be authenticated with the user that uploads the document and the document id.

#### HTTP Request

`GET http://api.dialogram.fr:8080/api/document/:idDocument`

#### Query Parameters

NONE

<aside class="success">
Remember — a happy user is an authenticated user by token!
</aside>


## Get User Documents

```shell
curl -X GET \
  http://api.dialogram.fr:8080/api/user/document \
  -H 'Authorization: Bearer <your_access_token>' \
  -H 'Postman-Token: 5127421b-d83a-4730-b9b8-7a20955dac1c' \
  -H 'cache-control: no-cache'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://api.dialogram.fr:8080/api/user/document",
  "method": "GET",
  "headers": {
    "Authorization": "Bearer <your_access_token>",
    "cache-control": "no-cache",
    "Postman-Token": "59497a27-d494-4bf5-a225-db888692d29a"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above request returns a JSON structured like this:

```json
{
    "data": [
        {
            "type": "documents",
            "id": "5c2e260e581ae035587a4346",
            "name": "PLD Dialogram",
            "link": "http://api.dialogram.fr:8080/medias/1546528270492-PLD_DIALOGRAM.pdf?accessToken=<your_access_token>",
            "usageName": "<timestamp>-<file_name>.pdf",
            "nbPage": 23,
            "public": false,
            "description": null,
            "status": -1,
            "category": "health",
            "idTranslation": null,
            "idOwner": "5c2e2528581ae035587a4344",
            "creationDate": "2019-01-29T19:31:06.424Z"
        },
        {
            "type": "documents",
            "id": "5c2e349d1679630b18f5636f",
            "name": "Insurance file",
            "link": "http://api.dialogram.fr:8080/medias/1546531997311-INSURANCE_FILE.pdf?accessToken=<your_access_token>",
            "usageName": "<timestamp>-<file_name>.pdf",
            "nbPage": 2,
            "public": false,
            "description": "Medical insurance company",
            "status": -1,
            "category": "health",
            "idTranslation": null,
            "idOwner": "5c2e2528581ae035587a4344",
            "creationDate": "2019-01-29T19:31:06.424Z"
        }
    ],
    "includes": []
}
```

This endpoint get all the user documents

#### HTTP Request

`GET http://api.dialogram.fr:8080/api/user/document`

#### Query Parameters

NONE

<aside class="success">
Remember — a happy user is an authenticated user by token!
</aside>


## Update PDF document

```shell
curl -X PUT \
  http://api.dialogram.fr:8080/api/document/update/:idDocument \
  -H 'Authorization: Bearer <your_access_token>' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
	     "name" : "newName",
	     "description": "Now we have a nice description, and the file is public",
	     "public" : "true",
       "category": "entertainment"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://api.dialogram.fr:8080/api/document/update/:idDocument",
  "method": "PUT",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Bearer <your_access_token>",
    "cache-control": "no-cache"
  },
  "processData": false,
  "data": "{\r\n\t    \"name\" : \"newName\",\r\n\t\t\"description\": \"Now we have a nice description, and the file is public\",\r\n\t    \"public\" : \"true\"\r\n}"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above request returns a JSON structured like this:

```json
{
    "data": [
        {
          "type": "documents",
          "id": "<document_id>",
          "name": "newName",
          "link": "api.dialogram.fr:8080/medias/<timestamp>-<file_name>.pdf?accessToken=<your_access_token>",
          "usageName": "<timestamp>-<file_name>.pdf",
          "nbPage": 35,
          "public": true,
          "description": "Now we have a nice description, and the file is public",
          "status": 1,
          "category": "entertainment",
          "idTranslation": null,
          "idOwner": "<owner_id>",
          "creationDate": "2019-01-29T19:31:06.424Z",
          "editDate": "2019-01-30T20:14:56.747Z"
        }
    ],
    "includes": []
}
```

This endpoint update the data file. You only need to be authenticated with the user that uploads the document and the document id. A new field "editDate" will be set with the date of edit.

#### HTTP Request

`PUT http://api.dialogram.fr:8080/api/document/update/:id`

#### Query Parameters
``
{
  "name" : "newName",
	"description": "Now we have a nice description, and the file is public",
	"public" : "true",
  "category" : "entertainment"
}
``

<aside class="success">
Remember — a happy user is an authenticated user by token!
</aside>

## Delete Document by ID

```shell
curl -X DELETE \
  http://api.dialogram.fr:8080/api/document/:idDocument \
  -H 'Authorization: Bearer <your_access_token>' \
  -H 'Postman-Token: f2472e62-d64f-496e-8190-a115225d1e94' \
  -H 'cache-control: no-cache'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://api.dialogram.fr:8080/api/document/:idDocument",
  "method": "DELETE",
  "headers": {
    "Authorization": "Bearer <your_access_token>",
    "cache-control": "no-cache",
    "Postman-Token": "b68839fd-bcdf-4ee8-ac90-8dd5c667eacc"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above request returns a JSON structured like this:

```json
{
    "data": [],
    "includes": []
}
```

This endpoint delete a document by ID.

#### HTTP Request

`DELETE http://api.dialogram.fr:8080/api/document/:idDocument`

#### Query Parameters

NONE

## Search document

```shell
curl -X GET \
  http://api.dialogram.fr:8080/api/document/search/health \
  -H 'Authorization: Bearer <your_access_token>' \
  -H 'Content-Type: application/json' \
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://api.dialogram.fr:8080/api/document/search/health",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Bearer <your_access_token>",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above request returns a JSON structured like this:

```json
{
    "data": [
        {
            "type": "documents",
            "id": "idDoc1",
            "name": "document1",
            "link": "link_to_document",
            "usageName": "1549878031571-document1.pdf",
            "nbPage": 35,
            "public": true,
            "description": "je suis un test contenant la recherche health",
            "status": -1,
            "category": "entertainment",
            "idTranslation": null,
            "idOwner": "idUser1",
            "creationDate": "2019-02-11T09:40:34.409Z",
            "timestamp": 1549876559
        },
        {
            "type": "documents",
            "id": "idDoc2",
            "name": "document2",
            "link": "link_to_document",
            "usageName": "1549878041525-document2.pdf",
            "nbPage": 35,
            "public": true,
            "description": "moi aussi je suis un test",
            "status": -1,
            "category": "health",
            "idTranslation": null,
            "idOwner": "idUser2",
            "creationDate": "2019-02-11T09:40:43.471Z",
            "timestamp": 1549876559
        }
    ],
    "includes": []
}
```

This endpoint retrieve all the documents where there is occurences of the search query.
Note that the search query will be applied to the name, the description and the category of the document.

#### HTTP Request

`GET http://api.dialogram.fr:8080/api/document/search/:to_find`

#### Query Parameters

``
to_find: the string/character that will be search in all the documents in database.
``
