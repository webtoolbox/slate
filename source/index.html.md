---
title: Website Toolbox API v1
language_tabs:
  - shell: Curl
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
toc_footers: []
includes: [errors]
search: true
highlight_theme: darkula
---

# Website Toolbox API v1

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

The Website Toolbox API is organized around <a href="http://en.wikipedia.org/wiki/Representational_State_Transfer">REST</a>. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support <a href="http://en.wikipedia.org/wiki/Cross-origin_resource_sharing">cross-origin resource sharing</a>, allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website's client-side code). <a href="http://www.json.org/">JSON</a> is returned by all API responses, including errors.

Base URLs:

* <a href="https://api.websitetoolbox.com/v1">https://api.websitetoolbox.com/v1</a>



Web: <a href="https://www.websitetoolbox.com/contact">Support</a> 

# Authentication


* API Key
    - Parameter Name: **x-api-key**, in: header. Authenticate your account when using the API by including your secret API key in the HTTP headers of the request. You can manage your API keys in the Dashboard. Your API keys carry many privileges, so be sure to keep them secret! Do not share your secret API keys in publicly accessible areas such GitHub, client-side code, and so forth. All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.



# Categories

## getCategories

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/categories \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/categories',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/categories',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/categories', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/categories");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/categories`

*List categories*

Returns a list of categories. The categories are returned sorted by displayorder, minimum displayorder category appearing first.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description

> Example responses

```json
[
  {
    "categoryId": 0,
    "description": "string",
    "unlisted": true,
    "title": "string",
    "locked": true,
    "passwordProtected": true,
    "linked": "string",
    "parentId": 0,
    "object": "string"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[ListCategories](#schemalistcategories)

### Response Headers

Status|Header|Type|Format|Description
---|---|---|---|---|
200|Access-Control-Allow-Origin|string||

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## createCategory

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/categories \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "title": "string",
  "description": "string",
  "unlisted": true,
  "locked": true,
  "password": "string",
  "link": "string",
  "parentId": 0
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/categories',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/categories',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/categories', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/categories");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/categories`

*Create a category*

Creates a new category to the forum.

> Body parameter

```json
{
  "title": "string",
  "description": "string",
  "unlisted": true,
  "locked": true,
  "password": "string",
  "link": "string",
  "parentId": 0
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
body<br>[AddCategory](#schemaaddcategory)|No description
» title<br>string|This is the name of the category. It describes the theme of the discussions within the category in a concise manner.
» description<br>string|An arbitrary string which you can attach to a category object. It is displayed alongside the category in the web interface.
» unlisted<br>boolean|Boolean representing whether a category is unlisted or not. Unlisted will hide it on the category listing on forum.
» locked<br>boolean|Boolean representing whether a category is locked or not. Locked will prevent any new posts from being made in the category.
» password<br>string|It is used to password protect the category so only people with the correct password can enter.
» link<br>string|The category will not be a real category. Instead it will simply be a link to the URL you provide.
» parentId<br>integer|The categoryId of parent category.

> Example responses

```json
{
  "categoryId": 0,
  "description": "string",
  "unlisted": true,
  "title": "string",
  "locked": true,
  "passwordProtected": true,
  "linked": "string",
  "parentId": 0,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Category](#schemacategory)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

### Response Headers

Status|Header|Type|Format|Description
---|---|---|---|---|
200|Access-Control-Allow-Origin|string||

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getCategory

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/categories/{categoryId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/categories/{categoryId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/categories/{categoryId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/categories/{categoryId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/categories/{categoryId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/categories/{categoryId}`

*Retrieve a category*

Retrieves the details of an existing category. You need only supply the unique category identifier that was returned upon customer creation.

### Parameters

Fields|Description
---|---|
categoryId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
{
  "categoryId": 0,
  "description": "string",
  "unlisted": true,
  "title": "string",
  "locked": true,
  "passwordProtected": true,
  "linked": "string",
  "parentId": 0,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Category](#schemacategory)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|404 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## updateCategory

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/categories/{categoryId} \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "categoryId": 0,
  "description": "string",
  "unlisted": true,
  "title": "string",
  "locked": true,
  "passwordProtected": true,
  "linked": "string",
  "parentId": 0,
  "object": "string"
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/categories/{categoryId}',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/categories/{categoryId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/categories/{categoryId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/categories/{categoryId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/categories/{categoryId}`

*Update a category*

Updates the specified category by setting the values of the parameters passed. Any parameters not provided will be left unchanged. This request accepts mostly the same arguments as the category creation call.

> Body parameter

```json
{
  "categoryId": 0,
  "description": "string",
  "unlisted": true,
  "title": "string",
  "locked": true,
  "passwordProtected": true,
  "linked": "string",
  "parentId": 0,
  "object": "string"
}
```
### Parameters

Fields|Description
---|---|
categoryId<br>string|No description
x-api-key<br>string|No description
body<br>[Category](#schemacategory)|No description
» categoryId<br>integer|The unique identifier for a category.
» description<br>string|An arbitrary string which you can attach to a category object. It is displayed alongside the category in the web interface.
» unlisted<br>boolean|Boolean representing whether a category is unlisted or not. Unlisted will hide it on the category listing on forum.
» title<br>string|This is the name of the category. It describes the theme of the discussions within the category in a concise manner.
» locked<br>boolean|Boolean representing whether a category is locked or not. Locked will prevent any new posts from being made in the category.
» passwordProtected<br>boolean|Boolean representing whether a category is password protected or not. It is used to password protect the category so only people with the correct password can enter.
» linked<br>string|The category will not be a real category. Instead it will simply be a link to the URL you provide.
» parentId<br>integer|The categoryId of parent category.
» object<br>string|String representing the object’s type. Objects of the same type share the same value.

> Example responses

```json
{
  "categoryId": 0,
  "description": "string",
  "unlisted": true,
  "title": "string",
  "locked": true,
  "passwordProtected": true,
  "linked": "string",
  "parentId": 0,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Category](#schemacategory)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## deleteCategory

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.websitetoolbox.com/v1/api/categories/{categoryId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/categories/{categoryId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://api.websitetoolbox.com/v1/api/categories/{categoryId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.delete('https://api.websitetoolbox.com/v1/api/categories/{categoryId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/categories/{categoryId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /api/categories/{categoryId}`

*Delete a category*

Permanently deletes a category. It cannot be undone. Also immediately deletes any topics and posts on the category.

### Parameters

Fields|Description
---|---|
categoryId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
{
  "status": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[DeleteResponse](#schemadeleteresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Conversations

## getConversations

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/conversations \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/conversations',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/conversations',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/conversations', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/conversations");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/conversations`

*List conversations*

Returns a list of conversations. The conversations are returned sorted by creation date, with the most recent conversations appearing first.

### Parameters

Fields|Description
---|---|
userId<br>string|No description
limit<br>string|No description
page<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
[
  {
    "object": "string",
    "subject": "string",
    "dateTimestamp": 0,
    "participants": [
      {
        "userId": 0,
        "avatarUrl": "string",
        "active": true,
        "username": "string",
        "unreadCount": 0,
        "isStarter": true
      }
    ],
    "conversationId": 0
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[ListConversations](#schemalistconversations)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## createConversation

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/conversations \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "message": "string",
  "recipientUsernames": [
    "string"
  ],
  "subject": "string",
  "senderId": 0
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/conversations',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/conversations',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/conversations', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/conversations");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/conversations`

*Create a conversation*

Creates a new conversation  to the forum.

> Body parameter

```json
{
  "message": "string",
  "recipientUsernames": [
    "string"
  ],
  "subject": "string",
  "senderId": 0
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
body<br>[AddConversation](#schemaaddconversation)|No description
» message<br>string|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
» subject<br>string|Thing that is being discussed, described for conversation.
» senderId<br>integer|Sender's userId who started the conversation.
» recipientUsernames<br>[string]|A list of usernames who will receive the messages.

> Example responses

```json
{
  "object": "string",
  "subject": "string",
  "dateTimestamp": 0,
  "participants": [
    {
      "userId": 0,
      "avatarUrl": "string",
      "active": true,
      "username": "string",
      "unreadCount": 0,
      "isStarter": true
    }
  ],
  "conversationId": 0
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Conversation](#schemaconversation)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getConversation

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/conversations/{conversationId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/conversations/{conversationId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/conversations/{conversationId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/conversations/{conversationId}`

*Retrieve a conversation*

Retrieves the details of an existing conversation. You need only supply the unique conversation identifier that was returned upon conversation creation.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
conversationId<br>string|No description

> Example responses

```json
{
  "object": "string",
  "subject": "string",
  "dateTimestamp": 0,
  "participants": [
    {
      "userId": 0,
      "avatarUrl": "string",
      "active": true,
      "username": "string",
      "unreadCount": 0,
      "isStarter": true
    }
  ],
  "conversationId": 0
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Conversation](#schemaconversation)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|404 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## deleteConversation

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.websitetoolbox.com/v1/api/conversations/{conversationId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://api.websitetoolbox.com/v1/api/conversations/{conversationId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.delete('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/conversations/{conversationId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /api/conversations/{conversationId}`

*Delete a conversation*

Permanently deletes a customer. It cannot be undone.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
conversationId<br>string|No description

> Example responses

```json
{
  "status": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[DeleteResponse](#schemadeleteresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getMessages

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/conversations/{conversationId}/messages`

*List messages for a conversation*

Returns a list of your messages for a conversation. The messages are returned sorted by creation date, with the most recent messages appearing first.

### Parameters

Fields|Description
---|---|
userId<br>string|No description
limit<br>string|No description
page<br>string|No description
x-api-key<br>string|No description
conversationId<br>string|No description

> Example responses

```json
[
  {
    "sender": {
      "userId": 0,
      "username": "string"
    },
    "message": "string",
    "messageId": 0,
    "attachments": [
      {
        "fileName": "string",
        "URL": "string",
        "id": "string",
        "object": "string"
      }
    ],
    "dateTimestamp": 0,
    "object": "string"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[ListMessages](#schemalistmessages)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|404 response|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## updateMessages

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "message": "string",
  "userId": 0
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/conversations/{conversationId}/messages`

*Create a new message for a conversation*

Creates a new message

> Body parameter

```json
{
  "message": "string",
  "userId": 0
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
conversationId<br>string|No description
body<br>[AddMessage](#schemaaddmessage)|No description
» message<br>string|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
» userId<br>integer|The userId of member to create a message.

> Example responses

```json
{
  "sender": {
    "userId": 0,
    "username": "string"
  },
  "message": "string",
  "messageId": 0,
  "attachments": [
    {
      "fileName": "string",
      "URL": "string",
      "id": "string",
      "object": "string"
    }
  ],
  "dateTimestamp": 0,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Message](#schemamessage)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getMessage

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages/{messageId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages/{messageId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages/{messageId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages/{messageId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/conversations/{conversationId}/messages/{messageId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/conversations/{conversationId}/messages/{messageId}`

*Retrieve a message*

Retrieves the details of an existing message. You need only supply the unique message identifier that was returned upon message creation.

### Parameters

Fields|Description
---|---|
userId<br>string|No description
limit<br>string|No description
page<br>string|No description
messageId<br>string|No description
x-api-key<br>string|No description
conversationId<br>string|No description

> Example responses

```json
{
  "sender": {
    "userId": 0,
    "username": "string"
  },
  "message": "string",
  "messageId": 0,
  "attachments": [
    {
      "fileName": "string",
      "URL": "string",
      "id": "string",
      "object": "string"
    }
  ],
  "dateTimestamp": 0,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Message](#schemamessage)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Posts

## getPosts

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/posts \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/posts',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/posts',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/posts', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/posts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/posts`

*List posts*

Returns a list of posts. The posts are returned sorted by creation date, with the most recent posts appearing first.

### Parameters

Fields|Description
---|---|
userId<br>string|No description
topicId<br>string|No description
limit<br>string|No description
page<br>string|No description
x-api-key<br>string|No description
categoryId<br>string|No description

> Example responses

```json
[
  {
    "message": "string",
    "likeCount": 0,
    "postTimestamp": 0,
    "postId": 0,
    "dislikeCount": 0,
    "author": {
      "userId": 0,
      "avatarUrl": "string",
      "username": "string"
    },
    "attachments": [
      {
        "fileName": "string",
        "URL": "string",
        "id": "string"
      }
    ],
    "attachmentCount": 0,
    "pending": true,
    "object": "string"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[ListPosts](#schemalistposts)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## createPost

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/posts \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "content": "string",
  "username": "string",
  "topicId": 0
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/posts',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/posts',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/posts', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/posts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/posts`

*Create a post*

Creates a new post

> Body parameter

```json
{
  "content": "string",
  "username": "string",
  "topicId": 0
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
body<br>[AddPost](#schemaaddpost)|No description
» content<br>string|Content is usually a message, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
» username<br>string|The username of member to create this object.
» topicId<br>integer|The unique identifier of topic to create this object.

> Example responses

```json
{
  "message": "string",
  "likeCount": 0,
  "postTimestamp": 0,
  "postId": 0,
  "dislikeCount": 0,
  "author": {
    "userId": 0,
    "avatarUrl": "string",
    "username": "string"
  },
  "attachments": [
    {
      "fileName": "string",
      "URL": "string",
      "id": "string"
    }
  ],
  "attachmentCount": 0,
  "pending": true,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Post](#schemapost)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getPost

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/posts/{postId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/posts/{postId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/posts/{postId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/posts/{postId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/posts/{postId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/posts/{postId}`

*Retrieve a post*

Retrieves the details of an existing post. You need only supply the unique post identifier that was returned upon post creation.

### Parameters

Fields|Description
---|---|
postId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
{
  "message": "string",
  "likeCount": 0,
  "postTimestamp": 0,
  "postId": 0,
  "dislikeCount": 0,
  "author": {
    "userId": 0,
    "avatarUrl": "string",
    "username": "string"
  },
  "attachments": [
    {
      "fileName": "string",
      "URL": "string",
      "id": "string"
    }
  ],
  "attachmentCount": 0,
  "pending": true,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Post](#schemapost)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|404 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## updatePost

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/posts/{postId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/posts/{postId}',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/posts/{postId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/posts/{postId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/posts/{postId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/posts/{postId}`

*Update a post*

Updates the specified post by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

### Parameters

Fields|Description
---|---|
postId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
{
  "message": "string",
  "likeCount": 0,
  "postTimestamp": 0,
  "postId": 0,
  "dislikeCount": 0,
  "author": {
    "userId": 0,
    "avatarUrl": "string",
    "username": "string"
  },
  "attachments": [
    {
      "fileName": "string",
      "URL": "string",
      "id": "string"
    }
  ],
  "attachmentCount": 0,
  "pending": true,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Post](#schemapost)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## deletePost

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.websitetoolbox.com/v1/api/posts/{postId} \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/posts/{postId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://api.websitetoolbox.com/v1/api/posts/{postId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.delete('https://api.websitetoolbox.com/v1/api/posts/{postId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/posts/{postId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /api/posts/{postId}`

*Delete a post*

Permanently deletes a post. It cannot be undone. Also immediately deletes any attachments on the post.

### Parameters

Fields|Description
---|---|
postId<br>string|No description

> Example responses

```json
{
  "status": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[DeleteResponse](#schemadeleteresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Topics

## getTopics

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/topics \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/topics',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/topics',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/topics', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/topics");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/topics`

*List topics*

Returns a list of topics. The topics are returned sorted by creation date, with the most recent topics appearing first.

### Parameters

Fields|Description
---|---|
userId<br>string|No description
limit<br>string|No description
sort<br>string|No description
page<br>string|No description
x-api-key<br>string|No description
categoryId<br>string|No description

> Example responses

```json
[
  {
    "lastPost": {
      "author": {
        "avatarUrl": "string",
        "userId": 0,
        "username": "string"
      },
      "timestamp": 0,
      "postId": 0
    },
    "viewCount": 0,
    "firstPostId": 0,
    "locked": true,
    "postCount": 0,
    "replyCount": 0,
    "pinned": true,
    "topicId": 0,
    "title": "string",
    "author": {
      "avatarUrl": "string",
      "username": "string",
      "userId": 0
    },
    "categoryId": 0,
    "dateTimestamp": 0,
    "object": "string"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[ListTopics](#schemalisttopics)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## createTopic

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/topics \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "title": "string",
  "content": "string",
  "username": "string",
  "categoryId": 0
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/topics',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/topics',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/topics', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/topics");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/topics`

*Create a topic*

Creates a new topic

> Body parameter

```json
{
  "title": "string",
  "content": "string",
  "username": "string",
  "categoryId": 0
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
body<br>[AddTopic](#schemaaddtopic)|No description
» title<br>string|Thing that is being discussed, described for topic.
» content<br>string|Content is usually a message, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
» username<br>string|The username of member to create this object.
» categoryId<br>integer|The unique identifier of category to create this object.

> Example responses

```json
{
  "lastPost": {
    "author": {
      "avatarUrl": "string",
      "userId": 0,
      "username": "string"
    },
    "timestamp": 0,
    "postId": 0
  },
  "viewCount": 0,
  "firstPostId": 0,
  "locked": true,
  "postCount": 0,
  "replyCount": 0,
  "pinned": true,
  "topicId": 0,
  "title": "string",
  "author": {
    "avatarUrl": "string",
    "username": "string",
    "userId": 0
  },
  "categoryId": 0,
  "dateTimestamp": 0,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Topic](#schematopic)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getTopic

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/topics/{topicId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/topics/{topicId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/topics/{topicId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/topics/{topicId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/topics/{topicId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/topics/{topicId}`

*Retrieve a topic*

Retrieves the details of an existing topic. You need only supply the unique topic identifier that was returned upon topic creation.

### Parameters

Fields|Description
---|---|
topicId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
{
  "lastPost": {
    "author": {
      "avatarUrl": "string",
      "userId": 0,
      "username": "string"
    },
    "timestamp": 0,
    "postId": 0
  },
  "viewCount": 0,
  "firstPostId": 0,
  "locked": true,
  "postCount": 0,
  "replyCount": 0,
  "pinned": true,
  "topicId": 0,
  "title": "string",
  "author": {
    "avatarUrl": "string",
    "username": "string",
    "userId": 0
  },
  "categoryId": 0,
  "dateTimestamp": 0,
  "object": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Topic](#schematopic)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|404 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## updateTopic

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/topics/{topicId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/topics/{topicId}',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/topics/{topicId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/topics/{topicId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/topics/{topicId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/topics/{topicId}`

*Update a topic*

Updates the specified topic by setting the values of the parameters passed. Any parameters not provided will be left unchanged. <p>This request accepts mostly the same arguments as the topic creation call.</p>

### Parameters

Fields|Description
---|---|
topicId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
{
  "lastPost": {
    "author": {
      "avatarUrl": "string",
      "userId": 0,
      "username": "string"
    },
    "timestamp": 0,
    "postId": 0
  },
  "viewCount": 0,
  "firstPostId": 0,
  "locked": true,
  "postCount": 0,
  "replyCount": 0,
  "pinned": true,
  "topicId": 0,
  "title": "string",
  "author": {
    "avatarUrl": "string",
    "username": "string",
    "userId": 0
  },
  "categoryId": 0,
  "dateTimestamp": 0,
  "object": "string"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Topic](#schematopic)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## deleteTopic

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.websitetoolbox.com/v1/api/topics/{topicId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/topics/{topicId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://api.websitetoolbox.com/v1/api/topics/{topicId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.delete('https://api.websitetoolbox.com/v1/api/topics/{topicId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/topics/{topicId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /api/topics/{topicId}`

*Delete a topic*

Permanently deletes a topic. It cannot be undone. Also immediately deletes all posts in the topic.

### Parameters

Fields|Description
---|---|
topicId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
{
  "status": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[DeleteResponse](#schemadeleteresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Usergroups

## getUsergroups

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/usergroups \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/usergroups',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/usergroups',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/usergroups', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/usergroups");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/usergroups`

*List usergroups*

Returns a list of all usergroups.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description

> Example responses

```json
[
  {
    "usergroupId": 0,
    "title": "string",
    "object": "string",
    "requireEventApproval": true,
    "viewInvisibleMembers": true,
    "viewOthersTopics": true,
    "viewableOnMembersList": true,
    "uploadAttachments": true,
    "changeUsername": true,
    "defaultGroup": true,
    "viewForum": true,
    "startTopics": true,
    "deleteOwnTopics": true,
    "createAlbums": true,
    "moveOwnTopics": true,
    "viewAttachments": true,
    "editOwnProfile": true,
    "customTitle": true,
    "viewAlbums": true,
    "signature": true,
    "viewTopicContent": true,
    "setSelfAsInvisible": true,
    "editOwnImages": true,
    "requirePostApproval": true,
    "viewCalendar": true,
    "moderateAlbums": true,
    "editOwnPosts": true,
    "postEvents": true,
    "viewCategory": true,
    "viewProfiles": true,
    "editOwnEvents": true,
    "replyOwnTopics": true,
    "viewOthersEvents": true,
    "replyTopics": true,
    "deleteOwnPosts": true,
    "deleteOwnEvents": true,
    "deleteOwnImages": true,
    "deleteOwnProfile": true
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[ListUsergroups](#schemalistusergroups)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## createUsergroup

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/usergroups \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "title": "string",
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true,
  "requireEventApproval": true
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/usergroups',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/usergroups',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/usergroups', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/usergroups");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/usergroups`

*Create a usergroup*

Creates a custom usergroup

> Body parameter

```json
{
  "title": "string",
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true,
  "requireEventApproval": true
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
body<br>[AddUsergroup](#schemaaddusergroup)|No description
» title<br>string|This is the name of usergroup. It is not shown to members but used to identify in User Group Manager.
» viewInvisibleMembers<br>boolean|The viewInvisibleMembers permission to create this object.
» viewOthersTopics<br>boolean|The viewOthersTopics permission to create this object.
» viewableOnMembersList<br>boolean|The viewableOnMembersList permission to create this object.
» uploadAttachments<br>boolean|The uploadAttachments permission to create this object.
» changeUsername<br>boolean|The changeUsername permission to create this object.
» viewForum<br>boolean|The viewForum permission to create this object.
» startTopics<br>boolean|The startTopics permission to create this object.
» deleteOwnTopics<br>boolean|The deleteOwnTopics permission to create this object.
» createAlbums<br>boolean|The createAlbums permission to create this object.
» moveOwnTopics<br>boolean|The moveOwnTopics permission to create this object.
» viewAttachments<br>boolean|The viewAttachments permission to create this object.
» editOwnProfile<br>boolean|The editOwnProfile permission to create this object.
» customTitle<br>boolean|The customTitle permission to create this object.
» viewAlbums<br>boolean|The viewAlbums permission to create this object.
» signature<br>boolean|The signature permission to create this object.
» viewTopicContent<br>boolean|The viewTopicContent permission to create this object.
» setSelfAsInvisible<br>boolean|The setSelfAsInvisible permission to create this object.
» editOwnImages<br>boolean|The editOwnImages permission to create this object.
» requirePostApproval<br>boolean|The requirePostApproval permission to create this object.
» viewCalendar<br>boolean|The viewCalendar permission to create this object.
» moderateAlbums<br>boolean|The moderateAlbums permission to create this object.
» editOwnPosts<br>boolean|The editOwnPosts permission to create this object.
» postEvents<br>boolean|The postEvents permission to create this object.
» viewCategory<br>boolean|The viewCategory permission to create this object.
» viewProfiles<br>boolean|The viewProfiles permission to create this object.
» editOwnEvents<br>boolean|The editOwnEvents permission to create this object.
» replyOwnTopics<br>boolean|The replyOwnTopics permission to create this object.
» viewOthersEvents<br>boolean|The viewOthersEvents permission to create this object.
» replyTopics<br>boolean|The replyTopics permission to create this object.
» deleteOwnPosts<br>boolean|The deleteOwnPosts permission to create this object.
» deleteOwnEvents<br>boolean|The deleteOwnEvents permission to create this object.
» deleteOwnImages<br>boolean|The deleteOwnImages permission to create this object.
» deleteOwnProfile<br>boolean|The deleteOwnProfile permission to create this object.
» requireEventApproval<br>boolean|The requireEventApproval permission to create this object.

> Example responses

```json
{
  "usergroupId": 0,
  "title": "string",
  "object": "string",
  "requireEventApproval": true,
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "defaultGroup": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Usergroup](#schemausergroup)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getUsergroup

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/usergroups/{usergroupId}`

*Retrieve a usergroup*

Retrieves the details of an existing usergroup. You need only supply the unique usergroup identifier.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
usergroupId<br>string|No description

> Example responses

```json
{
  "usergroupId": 0,
  "title": "string",
  "object": "string",
  "requireEventApproval": true,
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "defaultGroup": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Usergroup](#schemausergroup)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|404 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## updateUsergroup

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId} \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "usergroupId": 0,
  "title": "string",
  "object": "string",
  "requireEventApproval": true,
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "defaultGroup": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/usergroups/{usergroupId}`

*Update a usergroup*

Creates a new category

> Body parameter

```json
{
  "usergroupId": 0,
  "title": "string",
  "object": "string",
  "requireEventApproval": true,
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "defaultGroup": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
usergroupId<br>string|No description
body<br>[Usergroup](#schemausergroup)|No description
» usergroupId<br>integer|The unique identifier for a usergroup.
» title<br>string|This is the name of usergroup. It is not shown to members but used to identify in User Group Manager.
» object<br>string|String representing the object’s type. Objects of the same type share the same value.
» requireEventApproval<br>boolean|Boolean representing whether requireEventApproval permission is enabled or not.
» viewInvisibleMembers<br>boolean|Boolean representing whether viewInvisibleMembers permission is enabled or not.
» viewOthersTopics<br>boolean|Boolean representing whether viewOthersTopics permission is enabled or not.
» viewableOnMembersList<br>boolean|Boolean representing whether viewableOnMembersList permission is enabled or not.
» uploadAttachments<br>boolean|Boolean representing whether uploadAttachments permission is enabled or not.
» changeUsername<br>boolean|Boolean representing whether changeUsername permission is enabled or not.
» defaultGroup<br>boolean|Boolean representing whether defaultGroup permission is enabled or not.
» viewForum<br>boolean|Boolean representing whether viewForum permission is enabled or not.
» startTopics<br>boolean|Boolean representing whether startTopics permission is enabled or not.
» deleteOwnTopics<br>boolean|Boolean representing whether deleteOwnTopics permission is enabled or not.
» createAlbums<br>boolean|Boolean representing whether createAlbums permission is enabled or not.
» moveOwnTopics<br>boolean|Boolean representing whether moveOwnTopics permission is enabled or not.
» viewAttachments<br>boolean|Boolean representing whether viewAttachments permission is enabled or not.
» editOwnProfile<br>boolean|Boolean representing whether editOwnProfile permission is enabled or not.
» customTitle<br>boolean|Boolean representing whether customTitle permission is enabled or not.
» viewAlbums<br>boolean|Boolean representing whether viewAlbums permission is enabled or not.
» signature<br>boolean|Boolean representing whether signature permission is enabled or not.
» viewTopicContent<br>boolean|Boolean representing whether viewTopicContent permission is enabled or not.
» setSelfAsInvisible<br>boolean|Boolean representing whether setSelfAsInvisible permission is enabled or not.
» editOwnImages<br>boolean|Boolean representing whether editOwnImages permission is enabled or not.
» requirePostApproval<br>boolean|Boolean representing whether requirePostApproval permission is enabled or not.
» viewCalendar<br>boolean|Boolean representing whether viewCalendar permission is enabled or not.
» moderateAlbums<br>boolean|Boolean representing whether moderateAlbums permission is enabled or not.
» editOwnPosts<br>boolean|Boolean representing whether editOwnPosts permission is enabled or not.
» postEvents<br>boolean|Boolean representing whether postEvents permission is enabled or not.
» viewCategory<br>boolean|Boolean representing whether viewCategory permission is enabled or not.
» viewProfiles<br>boolean|Boolean representing whether viewProfiles permission is enabled or not.
» editOwnEvents<br>boolean|Boolean representing whether editOwnEvents permission is enabled or not.
» replyOwnTopics<br>boolean|Boolean representing whether replyOwnTopics permission is enabled or not.
» viewOthersEvents<br>boolean|Boolean representing whether viewOthersEvents permission is enabled or not.
» replyTopics<br>boolean|Boolean representing whether replyTopics permission is enabled or not.
» deleteOwnPosts<br>boolean|Boolean representing whether deleteOwnPosts permission is enabled or not.
» deleteOwnEvents<br>boolean|Boolean representing whether deleteOwnEvents permission is enabled or not.
» deleteOwnImages<br>boolean|Boolean representing whether deleteOwnImages permission is enabled or not.
» deleteOwnProfile<br>boolean|Boolean representing whether deleteOwnProfile permission is enabled or not.

> Example responses

```json
{
  "usergroupId": 0,
  "title": "string",
  "object": "string",
  "requireEventApproval": true,
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "defaultGroup": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[Usergroup](#schemausergroup)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## deleteUsergroup

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.delete('https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/usergroups/{usergroupId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /api/usergroups/{usergroupId}`

*Delete a custom usergroup*

Permanently deletes a custom usergroup. It cannot be undone.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
usergroupId<br>string|No description

> Example responses

```json
{
  "status": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[DeleteResponse](#schemadeleteresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Users

## getUsers

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/users \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/users',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/users',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/users', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/users");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/users`

*List users*

Returns a list of users on forum. The users are returned sorted by creation date, with the most recent users appearing first.

### Parameters

Fields|Description
---|---|
limit<br>string|No description
page<br>string|No description
userGroupId<br>string|No description
x-api-key<br>string|No description

> Example responses

```json
[
  {
    "userId": 0,
    "allowEmails": true,
    "userTitle": "string",
    "avatarUrl": "string",
    "reputation": 0,
    "userGroups": [],
    "instantMessagingType": "string",
    "joinDateTimestamp": 0,
    "lastPostTimestamp": 0,
    "name": "string",
    "invisible": true,
    "enableMessages": true,
    "username": "string",
    "postCount": 0,
    "signature": "string",
    "email": "string",
    "object": "string",
    "lastVisitTimestamp": 0,
    "customFields": [],
    "instantMessagingId": "string"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[ListUsers](#schemalistusers)

### Response Headers

Status|Header|Type|Format|Description
---|---|---|---|---|
200|Access-Control-Allow-Origin|string||

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## createUser

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/users \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "username": "string",
  "password": "string",
  "email": "string",
  "userGroupId": 0,
  "signature": "string",
  "name": "string",
  "instantMessagingType": "string",
  "instantMessagingId": "string",
  "birthday": "string",
  "field[ID]": "string"
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/users',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/users',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/users', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/users");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/users`

*Add a new user to the forum*

Creates a new user  on forum

> Body parameter

```json
{
  "username": "string",
  "password": "string",
  "email": "string",
  "userGroupId": 0,
  "signature": "string",
  "name": "string",
  "instantMessagingType": "string",
  "instantMessagingId": "string",
  "birthday": "string",
  "field[ID]": "string"
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
body<br>[AddUser](#schemaadduser)|No description
» username<br>string|The username of the member.
» password<br>string|The password of the member.
» email<br>string|The email address of the member. 
» userGroupId<br>integer|The userGroupId of the member.
» signature<br>string|Signature of member.
» name<br>string|The name of the member.
» instantMessagingType<br>string|Instant messaging type of the member.
» instantMessagingId<br>string|Instant messaging id of the member.
» birthday<br>string|Birthday of the member.
» field[ID]<br>string|A custom field belongs to the member where [ID] is the custom profile fieldid. You can replace ID with the custom field value to update the custom fields e.g. field102901.

> Example responses

```json
{
  "userId": 0,
  "allowEmails": true,
  "userTitle": "string",
  "avatarUrl": "string",
  "reputation": 0,
  "userGroups": [],
  "instantMessagingType": "string",
  "joinDateTimestamp": 0,
  "lastPostTimestamp": 0,
  "name": "string",
  "invisible": true,
  "enableMessages": true,
  "username": "string",
  "postCount": 0,
  "signature": "string",
  "email": "string",
  "object": "string",
  "lastVisitTimestamp": 0,
  "customFields": [],
  "instantMessagingId": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[User](#schemauser)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

### Response Headers

Status|Header|Type|Format|Description
---|---|---|---|---|
200|Access-Control-Allow-Origin|string||

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## getUser

> Code samples

```shell
# You can also use wget
curl -X GET https://api.websitetoolbox.com/v1/api/users/{userId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/users/{userId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.websitetoolbox.com/v1/api/users/{userId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.get('https://api.websitetoolbox.com/v1/api/users/{userId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /api/users/{userId}`

*Retrieve a user*

Retrieves the details of an existing user. You need only supply the unique user identifier that was returned upon user creation.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
userId<br>string|No description

> Example responses

```json
{
  "userId": 0,
  "allowEmails": true,
  "userTitle": "string",
  "avatarUrl": "string",
  "reputation": 0,
  "userGroups": [],
  "instantMessagingType": "string",
  "joinDateTimestamp": 0,
  "lastPostTimestamp": 0,
  "name": "string",
  "invisible": true,
  "enableMessages": true,
  "username": "string",
  "postCount": 0,
  "signature": "string",
  "email": "string",
  "object": "string",
  "lastVisitTimestamp": 0,
  "customFields": [],
  "instantMessagingId": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[User](#schemauser)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|404 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## updateUser

> Code samples

```shell
# You can also use wget
curl -X POST https://api.websitetoolbox.com/v1/api/users/{userId} \
  -H 'x-api-key: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "username": "string",
  "password": "string",
  "email": "string",
  "userGroups": [],
  "signature": "string",
  "name": "string",
  "instantMessagingType": "string",
  "lastPostTimestamp": 0,
  "instantMessagingId": "string",
  "birthday": "string",
  "field[ID]": "string"
}';
const headers = {
  'x-api-key':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/users/{userId}',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.websitetoolbox.com/v1/api/users/{userId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.websitetoolbox.com/v1/api/users/{userId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /api/users/{userId}`

*Update a user*

Updates the specified user by setting the values of the parameters passed. Any parameters not provided will be left unchanged. <p>This request accepts mostly the same arguments as the user creation call.</p>

> Body parameter

```json
{
  "username": "string",
  "password": "string",
  "email": "string",
  "userGroups": [],
  "signature": "string",
  "name": "string",
  "instantMessagingType": "string",
  "lastPostTimestamp": 0,
  "instantMessagingId": "string",
  "birthday": "string",
  "field[ID]": "string"
}
```
### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
userId<br>string|No description
body<br>[UpdateUser](#schemaupdateuser)|No description
» username<br>string|The username of member.
» password<br>string|The password of member.
» email<br>string|The email address of the member.
» signature<br>string|Signature of member.
» name<br>string|The name of member.
» instantMessagingType<br>string|Instant messaging type of the member.
» lastPostTimestamp<br>integer|Instant messaging type of member.
» instantMessagingId<br>string|Instant messaging id of member.
» birthday<br>string|Birthday of the member.
» field[ID]<br>string|A custom field belongs to the member where [ID] is the custom profile fieldid. You can replace ID with the custom field value to update the custom fields e.g. field102901.

> Example responses

```json
{
  "userId": 0,
  "allowEmails": true,
  "userTitle": "string",
  "avatarUrl": "string",
  "reputation": 0,
  "userGroups": [],
  "instantMessagingType": "string",
  "joinDateTimestamp": 0,
  "lastPostTimestamp": 0,
  "name": "string",
  "invisible": true,
  "enableMessages": true,
  "username": "string",
  "postCount": 0,
  "signature": "string",
  "email": "string",
  "object": "string",
  "lastVisitTimestamp": 0,
  "customFields": [],
  "instantMessagingId": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[User](#schemauser)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## deleteUser

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.websitetoolbox.com/v1/api/users/{userId} \
  -H 'x-api-key: string' \
  -H 'Accept: application/json'

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'x-api-key':'string',
  'Accept':'application/json'

};

fetch('https://api.websitetoolbox.com/v1/api/users/{userId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'x-api-key' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://api.websitetoolbox.com/v1/api/users/{userId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'x-api-key': 'string',
  'Accept': 'application/json'
}

r = requests.delete('https://api.websitetoolbox.com/v1/api/users/{userId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.websitetoolbox.com/v1/api/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /api/users/{userId}`

*Delete a user*

Permanently deletes a user. It cannot be undone.

### Parameters

Fields|Description
---|---|
x-api-key<br>string|No description
userId<br>string|No description

> Example responses

```json
{
  "status": "string"
}
```
```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|200 response|[DeleteResponse](#schemadeleteresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|400 response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Schemas

## AddPost

<a name="schemaaddpost"></a>

```json
{
  "content": "string",
  "username": "string",
  "topicId": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
content|string|true|Content is usually a message, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
username|string|true|The username of member to create this object.
topicId|integer|true|The unique identifier of topic to create this object.



## ListTopics

<a name="schemalisttopics"></a>

```json
[
  {
    "lastPost": {
      "author": {
        "avatarUrl": "string",
        "userId": 0,
        "username": "string"
      },
      "timestamp": 0,
      "postId": 0
    },
    "viewCount": 0,
    "firstPostId": 0,
    "locked": true,
    "postCount": 0,
    "replyCount": 0,
    "pinned": true,
    "topicId": 0,
    "title": "string",
    "author": {
      "avatarUrl": "string",
      "username": "string",
      "userId": 0
    },
    "categoryId": 0,
    "dateTimestamp": 0,
    "object": "string"
  }
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[object]|false|No description
» lastPost|object|false|Last post of object.
»» author|object|false|No description
»»» avatarUrl|string|false|The URL of an icon or image representing a particular member in forum who created last post.
»»» userId|integer|false|The userId of member who created last post.
»»» username|string|false|The username of member who created last post.
»» timestamp|integer|false|Time at which the last post was created. Measured in seconds since the Unix epoch.
»» postId|integer|false|The unique identifier for a post.
» viewCount|integer|false|The number of views in topic.
» firstPostId|integer|false|The unique identifier of first post in topic.
» locked|boolean|false|Boolean representing whether a topic is locked or not. Locked will prevent any new posts from being made in the topic.
» postCount|integer|false|The number of posts in topic.
» replyCount|integer|false|The number of replies in topic.
» pinned|boolean|false|Boolean representing whether a topic is pinned or not. Pinned topic display at the beginning of that forum's topic listing to ensure that it receives attention from forum users.
» topicId|integer|false|The unique identifier for a topic.
» title|string|false|Thing that is being discussed, described for topic.
» author|object|false|The member who created this object.
»» avatarUrl|string|false|The URL of an icon or image representing a particular member in forum who created this object.
»» username|string|false|The username of member who created this object.
»» userId|integer|false|The userId of member who created this object.
» categoryId|integer|false|The unique identifier of category that belongs to this object.
» dateTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
» object|string|false|String representing the object’s type. Objects of the same type share the same value.



## ListUsergroups

<a name="schemalistusergroups"></a>

```json
[
  {
    "usergroupId": 0,
    "title": "string",
    "object": "string",
    "requireEventApproval": true,
    "viewInvisibleMembers": true,
    "viewOthersTopics": true,
    "viewableOnMembersList": true,
    "uploadAttachments": true,
    "changeUsername": true,
    "defaultGroup": true,
    "viewForum": true,
    "startTopics": true,
    "deleteOwnTopics": true,
    "createAlbums": true,
    "moveOwnTopics": true,
    "viewAttachments": true,
    "editOwnProfile": true,
    "customTitle": true,
    "viewAlbums": true,
    "signature": true,
    "viewTopicContent": true,
    "setSelfAsInvisible": true,
    "editOwnImages": true,
    "requirePostApproval": true,
    "viewCalendar": true,
    "moderateAlbums": true,
    "editOwnPosts": true,
    "postEvents": true,
    "viewCategory": true,
    "viewProfiles": true,
    "editOwnEvents": true,
    "replyOwnTopics": true,
    "viewOthersEvents": true,
    "replyTopics": true,
    "deleteOwnPosts": true,
    "deleteOwnEvents": true,
    "deleteOwnImages": true,
    "deleteOwnProfile": true
  }
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[object]|false|No description
» usergroupId|integer|false|The unique identifier for a usergroup.
» title|string|false|This is the name of usergroup. It is not shown to members but used to identify in User Group Manager.
» object|string|false|String representing the object’s type. Objects of the same type share the same value.
» requireEventApproval|boolean|false|Boolean representing whether requireEventApproval permission is enabled or not.
» viewInvisibleMembers|boolean|false|Boolean representing whether viewInvisibleMembers permission is enabled or not.
» viewOthersTopics|boolean|false|Boolean representing whether viewOthersTopics permission is enabled or not.
» viewableOnMembersList|boolean|false|Boolean representing whether viewableOnMembersList permission is enabled or not.
» uploadAttachments|boolean|false|Boolean representing whether uploadAttachments permission is enabled or not.
» changeUsername|boolean|false|Boolean representing whether changeUsername permission is enabled or not.
» defaultGroup|boolean|false|Boolean representing whether defaultGroup permission is enabled or not.
» viewForum|boolean|false|Boolean representing whether viewForum permission is enabled or not.
» startTopics|boolean|false|Boolean representing whether startTopics permission is enabled or not.
» deleteOwnTopics|boolean|false|Boolean representing whether deleteOwnTopics permission is enabled or not.
» createAlbums|boolean|false|Boolean representing whether createAlbums permission is enabled or not.
» moveOwnTopics|boolean|false|Boolean representing whether moveOwnTopics permission is enabled or not.
» viewAttachments|boolean|false|Boolean representing whether viewAttachments permission is enabled or not.
» editOwnProfile|boolean|false|Boolean representing whether editOwnProfile permission is enabled or not.
» customTitle|boolean|false|Boolean representing whether customTitle permission is enabled or not.
» viewAlbums|boolean|false|Boolean representing whether viewAlbums permission is enabled or not.
» signature|boolean|false|Boolean representing whether signature permission is enabled or not.
» viewTopicContent|boolean|false|Boolean representing whether viewTopicContent permission is enabled or not.
» setSelfAsInvisible|boolean|false|Boolean representing whether setSelfAsInvisible permission is enabled or not.
» editOwnImages|boolean|false|Boolean representing whether editOwnImages permission is enabled or not.
» requirePostApproval|boolean|false|Boolean representing whether requirePostApproval permission is enabled or not.
» viewCalendar|boolean|false|Boolean representing whether viewCalendar permission is enabled or not.
» moderateAlbums|boolean|false|Boolean representing whether moderateAlbums permission is enabled or not.
» editOwnPosts|boolean|false|Boolean representing whether editOwnPosts permission is enabled or not.
» postEvents|boolean|false|Boolean representing whether postEvents permission is enabled or not.
» viewCategory|boolean|false|Boolean representing whether viewCategory permission is enabled or not.
» viewProfiles|boolean|false|Boolean representing whether viewProfiles permission is enabled or not.
» editOwnEvents|boolean|false|Boolean representing whether editOwnEvents permission is enabled or not.
» replyOwnTopics|boolean|false|Boolean representing whether replyOwnTopics permission is enabled or not.
» viewOthersEvents|boolean|false|Boolean representing whether viewOthersEvents permission is enabled or not.
» replyTopics|boolean|false|Boolean representing whether replyTopics permission is enabled or not.
» deleteOwnPosts|boolean|false|Boolean representing whether deleteOwnPosts permission is enabled or not.
» deleteOwnEvents|boolean|false|Boolean representing whether deleteOwnEvents permission is enabled or not.
» deleteOwnImages|boolean|false|Boolean representing whether deleteOwnImages permission is enabled or not.
» deleteOwnProfile|boolean|false|Boolean representing whether deleteOwnProfile permission is enabled or not.



## Category

<a name="schemacategory"></a>

```json
{
  "categoryId": 0,
  "description": "string",
  "unlisted": true,
  "title": "string",
  "locked": true,
  "passwordProtected": true,
  "linked": "string",
  "parentId": 0,
  "object": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
categoryId|integer|false|The unique identifier for a category.
description|string|false|An arbitrary string which you can attach to a category object. It is displayed alongside the category in the web interface.
unlisted|boolean|false|Boolean representing whether a category is unlisted or not. Unlisted will hide it on the category listing on forum.
title|string|false|This is the name of the category. It describes the theme of the discussions within the category in a concise manner.
locked|boolean|false|Boolean representing whether a category is locked or not. Locked will prevent any new posts from being made in the category.
passwordProtected|boolean|false|Boolean representing whether a category is password protected or not. It is used to password protect the category so only people with the correct password can enter.
linked|string|false|The category will not be a real category. Instead it will simply be a link to the URL you provide.
parentId|integer|false|The categoryId of parent category.
object|string|false|String representing the object’s type. Objects of the same type share the same value.



## User

<a name="schemauser"></a>

```json
{
  "userId": 0,
  "allowEmails": true,
  "userTitle": "string",
  "avatarUrl": "string",
  "reputation": 0,
  "userGroups": [],
  "instantMessagingType": "string",
  "joinDateTimestamp": 0,
  "lastPostTimestamp": 0,
  "name": "string",
  "invisible": true,
  "enableMessages": true,
  "username": "string",
  "postCount": 0,
  "signature": "string",
  "email": "string",
  "object": "string",
  "lastVisitTimestamp": 0,
  "customFields": [],
  "instantMessagingId": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
userId|integer|false|The unique identifier of member that belongs to this object.
allowEmails|boolean|false|Boolean representing whether a member allow other members to send emails or not.
userTitle|string|false|The title of member.
avatarUrl|string|false|The URL of an icon or image representing the member in forum who created this object.
reputation|integer|false|It is a reputation score of member based on how much the community has liked their posts. The number of likes minus the number of dislikes a member's posts receive becomes their reputation score.
instantMessagingType|string|false|Instant messaging type of member.
joinDateTimestamp|integer|false|Time at which the member was created. Measured in seconds since the Unix epoch.
lastPostTimestamp|integer|false|Time at which the member was created last post. Measured in seconds since the Unix epoch.
name|string|false|The name of member.
invisible|boolean|false|Boolean representing whether a member is invisible or not. Invisible member browse the forum without other users knowing you are online.
enableMessages|boolean|false|Boolean representing whether a member has permission to send messages or not.
username|string|false|The username of member.
postCount|integer|false|The number of posts created by member.
signature|string|false|Signature of member.
email|string|false|The email address of the member.
object|string|false|String representing the object’s type. Objects of the same type share the same value.
lastVisitTimestamp|integer|false|Time at which the member was last visited. Measured in seconds since the Unix epoch.
instantMessagingId|string|false|Instant messaging id of member.



## ListUsers

<a name="schemalistusers"></a>

```json
[
  {
    "userId": 0,
    "allowEmails": true,
    "userTitle": "string",
    "avatarUrl": "string",
    "reputation": 0,
    "userGroups": [],
    "instantMessagingType": "string",
    "joinDateTimestamp": 0,
    "lastPostTimestamp": 0,
    "name": "string",
    "invisible": true,
    "enableMessages": true,
    "username": "string",
    "postCount": 0,
    "signature": "string",
    "email": "string",
    "object": "string",
    "lastVisitTimestamp": 0,
    "customFields": [],
    "instantMessagingId": "string"
  }
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[object]|false|No description
» userId|integer|false|The unique identifier of member that belongs to this object.
» allowEmails|boolean|false|Boolean representing whether a member allow other members to send emails or not.
» userTitle|string|false|The title of member.
» avatarUrl|string|false|The URL of an icon or image representing the member in forum who created this object.
» reputation|integer|false|It is a reputation score of member based on how much the community has liked their posts. The number of likes minus the number of dislikes a member's posts receive becomes their reputation score.
» instantMessagingType|string|false|Instant messaging type of member.
» joinDateTimestamp|integer|false|Time at which the member was created. Measured in seconds since the Unix epoch.
» lastPostTimestamp|integer|false|Time at which the member was created last post. Measured in seconds since the Unix epoch.
» name|string|false|The name of member.
» invisible|boolean|false|Boolean representing whether a member is invisible or not. Invisible member browse the forum without other users knowing you are online.
» enableMessages|boolean|false|Boolean representing whether a member has permission to send messages or not.
» username|string|false|Username of member.
» postCount|integer|false|The number of posts created by member.
» signature|string|false|Signature of member.
» email|string|false|Email address of member.
» object|string|false|String representing the object’s type. Objects of the same type share the same value.
» lastVisitTimestamp|integer|false|Time at which the member was last visited. Measured in seconds since the Unix epoch.
» instantMessagingId|string|false|Instant messaging id of member.



## Message

<a name="schemamessage"></a>

```json
{
  "sender": {
    "userId": 0,
    "username": "string"
  },
  "message": "string",
  "messageId": 0,
  "attachments": [
    {
      "fileName": "string",
      "URL": "string",
      "id": "string",
      "object": "string"
    }
  ],
  "dateTimestamp": 0,
  "object": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
sender|object|false|No description
» userId|integer|false|The userId of member who created this object.
» username|string|false|The username of member who created this object.
message|string|false|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
messageId|integer|false|The unique identifier for a message.
dateTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
object|string|false|String representing the object’s type. Objects of the same type share the same value.
attachments|[object]|false|No description
» fileName|string|false|The file name of attachment.
» URL|string|false|The attachment URL.
» id|string|false|The unique identifier for a attachment.
» object|string|false|String representing the object’s type. Objects of the same type share the same value.



## AddCategory

<a name="schemaaddcategory"></a>

```json
{
  "title": "string",
  "description": "string",
  "unlisted": true,
  "locked": true,
  "password": "string",
  "link": "string",
  "parentId": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
title|string|true|This is the name of the category. It describes the theme of the discussions within the category in a concise manner.
description|string|false|An arbitrary string which you can attach to a category object. It is displayed alongside the category in the web interface.
unlisted|boolean|false|Boolean representing whether a category is unlisted or not. Unlisted will hide it on the category listing on forum.
locked|boolean|false|Boolean representing whether a category is locked or not. Locked will prevent any new posts from being made in the category.
password|string|false|It is used to password protect the category so only people with the correct password can enter.
link|string|false|The category will not be a real category. Instead it will simply be a link to the URL you provide.
parentId|integer|false|The categoryId of parent category.



## ListCategories

<a name="schemalistcategories"></a>

```json
[
  {
    "categoryId": 0,
    "description": "string",
    "unlisted": true,
    "title": "string",
    "locked": true,
    "passwordProtected": true,
    "linked": "string",
    "parentId": 0,
    "object": "string"
  }
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[object]|false|No description
» categoryId|integer|false|The unique identifier for a category.
» description|string|false|An arbitrary string which you can attach to a category object. It is displayed alongside the category in the web interface.
» unlisted|boolean|false|Boolean representing whether a category is unlisted or not. Unlisted will hide it on the category listing on forum.
» title|string|false|This is the name of the category. It describes the theme of the discussions within the category in a concise manner.
» locked|boolean|false|Boolean representing whether a category is locked or not. Locked will prevent any new posts from being made in the category.
» passwordProtected|boolean|false|Boolean representing whether a category is password protected or not. It is used to password protect the category so only people with the correct password can enter.
» linked|string|false|The category will not be a real category. Instead it will simply be a link to the URL you provide.
» parentId|integer|false|The categoryId of parent category.
» object|string|false|String representing the object’s type. Objects of the same type share the same value.



## Post

<a name="schemapost"></a>

```json
{
  "message": "string",
  "likeCount": 0,
  "postTimestamp": 0,
  "postId": 0,
  "dislikeCount": 0,
  "author": {
    "userId": 0,
    "avatarUrl": "string",
    "username": "string"
  },
  "attachments": [
    {
      "fileName": "string",
      "URL": "string",
      "id": "string"
    }
  ],
  "attachmentCount": 0,
  "pending": true,
  "object": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
message|string|false|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
likeCount|integer|false|Total number of post likes.
postTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
postId|integer|false|The unique identifier of post
dislikeCount|integer|false|Total number of post dislikes.
author|object|false|No description
» userId|integer|false|The userId of member who created this object.
» avatarUrl|string|false|The URL of an icon or image representing a particular member in forum who created this object.
» username|string|false|The username of member who created this object.
attachmentCount|integer|false|Total number of attachments in post.
pending|boolean|false|Boolean representing whether a post is pending or not. Pending post will only be displayed after approval of moderator.
object|string|false|String representing the object’s type. Objects of the same type share the same value.
attachments|[object]|false|No description
» fileName|string|false|The file name of attachment.
» URL|string|false|The attachment URL.
» id|string|false|The unique identifier for a attachment.



## Error

<a name="schemaerror"></a>

```json
{
  "status": "string",
  "error": {
    "param": "string",
    "message": "string",
    "code": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
status|string|false|No description
error|object|false|No description
» param|string|false|The parameter the error relates to if the error is parameter-specific. 
» message|string|false|A human-readable message providing more details about the error.
» code|string|false|A short string related to error.



## Conversation

<a name="schemaconversation"></a>

```json
{
  "object": "string",
  "subject": "string",
  "dateTimestamp": 0,
  "participants": [
    {
      "userId": 0,
      "avatarUrl": "string",
      "active": true,
      "username": "string",
      "unreadCount": 0,
      "isStarter": true
    }
  ],
  "conversationId": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
object|string|false|String representing the object’s type. Objects of the same type share the same value.
subject|string|false|Thing that is being discussed, described for conversation.
dateTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
conversationId|integer|false|The unique identifier for a conversation.
participants|[object]|false|No description
» userId|integer|false|Participant's userId.
» avatarUrl|string|false|The URL of an icon or image representing a particular person in forum.
» active|boolean|false|Boolean representing whether a participant is active or not.
» username|string|false|Participant's username.
» unreadCount|integer|false|The number of unread messages in conversation.
» isStarter|boolean|false|Boolean representing whether a participant is started the conversation or not.



## Usergroup

<a name="schemausergroup"></a>

```json
{
  "usergroupId": 0,
  "title": "string",
  "object": "string",
  "requireEventApproval": true,
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "defaultGroup": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
usergroupId|integer|false|The unique identifier for a usergroup.
title|string|false|This is the name of usergroup. It is not shown to members but used to identify in User Group Manager.
object|string|false|String representing the object’s type. Objects of the same type share the same value.
requireEventApproval|boolean|false|Boolean representing whether requireEventApproval permission is enabled or not.
viewInvisibleMembers|boolean|false|Boolean representing whether viewInvisibleMembers permission is enabled or not.
viewOthersTopics|boolean|false|Boolean representing whether viewOthersTopics permission is enabled or not.
viewableOnMembersList|boolean|false|Boolean representing whether viewableOnMembersList permission is enabled or not.
uploadAttachments|boolean|false|Boolean representing whether uploadAttachments permission is enabled or not.
changeUsername|boolean|false|Boolean representing whether changeUsername permission is enabled or not.
defaultGroup|boolean|false|Boolean representing whether defaultGroup permission is enabled or not.
viewForum|boolean|false|Boolean representing whether viewForum permission is enabled or not.
startTopics|boolean|false|Boolean representing whether startTopics permission is enabled or not.
deleteOwnTopics|boolean|false|Boolean representing whether deleteOwnTopics permission is enabled or not.
createAlbums|boolean|false|Boolean representing whether createAlbums permission is enabled or not.
moveOwnTopics|boolean|false|Boolean representing whether moveOwnTopics permission is enabled or not.
viewAttachments|boolean|false|Boolean representing whether viewAttachments permission is enabled or not.
editOwnProfile|boolean|false|Boolean representing whether editOwnProfile permission is enabled or not.
customTitle|boolean|false|Boolean representing whether customTitle permission is enabled or not.
viewAlbums|boolean|false|Boolean representing whether viewAlbums permission is enabled or not.
signature|boolean|false|Boolean representing whether signature permission is enabled or not.
viewTopicContent|boolean|false|Boolean representing whether viewTopicContent permission is enabled or not.
setSelfAsInvisible|boolean|false|Boolean representing whether setSelfAsInvisible permission is enabled or not.
editOwnImages|boolean|false|Boolean representing whether editOwnImages permission is enabled or not.
requirePostApproval|boolean|false|Boolean representing whether requirePostApproval permission is enabled or not.
viewCalendar|boolean|false|Boolean representing whether viewCalendar permission is enabled or not.
moderateAlbums|boolean|false|Boolean representing whether moderateAlbums permission is enabled or not.
editOwnPosts|boolean|false|Boolean representing whether editOwnPosts permission is enabled or not.
postEvents|boolean|false|Boolean representing whether postEvents permission is enabled or not.
viewCategory|boolean|false|Boolean representing whether viewCategory permission is enabled or not.
viewProfiles|boolean|false|Boolean representing whether viewProfiles permission is enabled or not.
editOwnEvents|boolean|false|Boolean representing whether editOwnEvents permission is enabled or not.
replyOwnTopics|boolean|false|Boolean representing whether replyOwnTopics permission is enabled or not.
viewOthersEvents|boolean|false|Boolean representing whether viewOthersEvents permission is enabled or not.
replyTopics|boolean|false|Boolean representing whether replyTopics permission is enabled or not.
deleteOwnPosts|boolean|false|Boolean representing whether deleteOwnPosts permission is enabled or not.
deleteOwnEvents|boolean|false|Boolean representing whether deleteOwnEvents permission is enabled or not.
deleteOwnImages|boolean|false|Boolean representing whether deleteOwnImages permission is enabled or not.
deleteOwnProfile|boolean|false|Boolean representing whether deleteOwnProfile permission is enabled or not.



## AddUsergroup

<a name="schemaaddusergroup"></a>

```json
{
  "title": "string",
  "viewInvisibleMembers": true,
  "viewOthersTopics": true,
  "viewableOnMembersList": true,
  "uploadAttachments": true,
  "changeUsername": true,
  "viewForum": true,
  "startTopics": true,
  "deleteOwnTopics": true,
  "createAlbums": true,
  "moveOwnTopics": true,
  "viewAttachments": true,
  "editOwnProfile": true,
  "customTitle": true,
  "viewAlbums": true,
  "signature": true,
  "viewTopicContent": true,
  "setSelfAsInvisible": true,
  "editOwnImages": true,
  "requirePostApproval": true,
  "viewCalendar": true,
  "moderateAlbums": true,
  "editOwnPosts": true,
  "postEvents": true,
  "viewCategory": true,
  "viewProfiles": true,
  "editOwnEvents": true,
  "replyOwnTopics": true,
  "viewOthersEvents": true,
  "replyTopics": true,
  "deleteOwnPosts": true,
  "deleteOwnEvents": true,
  "deleteOwnImages": true,
  "deleteOwnProfile": true,
  "requireEventApproval": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
title|string|true|This is the name of usergroup. It is not shown to members but used to identify in User Group Manager.
viewInvisibleMembers|boolean|false|The viewInvisibleMembers permission to create this object.
viewOthersTopics|boolean|false|The viewOthersTopics permission to create this object.
viewableOnMembersList|boolean|false|The viewableOnMembersList permission to create this object.
uploadAttachments|boolean|false|The uploadAttachments permission to create this object.
changeUsername|boolean|false|The changeUsername permission to create this object.
viewForum|boolean|false|The viewForum permission to create this object.
startTopics|boolean|false|The startTopics permission to create this object.
deleteOwnTopics|boolean|false|The deleteOwnTopics permission to create this object.
createAlbums|boolean|false|The createAlbums permission to create this object.
moveOwnTopics|boolean|false|The moveOwnTopics permission to create this object.
viewAttachments|boolean|false|The viewAttachments permission to create this object.
editOwnProfile|boolean|false|The editOwnProfile permission to create this object.
customTitle|boolean|false|The customTitle permission to create this object.
viewAlbums|boolean|false|The viewAlbums permission to create this object.
signature|boolean|false|The signature permission to create this object.
viewTopicContent|boolean|false|The viewTopicContent permission to create this object.
setSelfAsInvisible|boolean|false|The setSelfAsInvisible permission to create this object.
editOwnImages|boolean|false|The editOwnImages permission to create this object.
requirePostApproval|boolean|false|The requirePostApproval permission to create this object.
viewCalendar|boolean|false|The viewCalendar permission to create this object.
moderateAlbums|boolean|false|The moderateAlbums permission to create this object.
editOwnPosts|boolean|false|The editOwnPosts permission to create this object.
postEvents|boolean|false|The postEvents permission to create this object.
viewCategory|boolean|false|The viewCategory permission to create this object.
viewProfiles|boolean|false|The viewProfiles permission to create this object.
editOwnEvents|boolean|false|The editOwnEvents permission to create this object.
replyOwnTopics|boolean|false|The replyOwnTopics permission to create this object.
viewOthersEvents|boolean|false|The viewOthersEvents permission to create this object.
replyTopics|boolean|false|The replyTopics permission to create this object.
deleteOwnPosts|boolean|false|The deleteOwnPosts permission to create this object.
deleteOwnEvents|boolean|false|The deleteOwnEvents permission to create this object.
deleteOwnImages|boolean|false|The deleteOwnImages permission to create this object.
deleteOwnProfile|boolean|false|The deleteOwnProfile permission to create this object.
requireEventApproval|boolean|false|The requireEventApproval permission to create this object.



## AddUser

<a name="schemaadduser"></a>

```json
{
  "username": "string",
  "password": "string",
  "email": "string",
  "userGroupId": 0,
  "signature": "string",
  "name": "string",
  "instantMessagingType": "string",
  "instantMessagingId": "string",
  "birthday": "string",
  "field[ID]": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
username|string|true|The username of the member.
password|string|true|The password of the member.
email|string|true|The email address of the member. 
userGroupId|integer|false|The userGroupId of the member.
signature|string|false|Signature of member.
name|string|false|The name of the member.
instantMessagingType|string|false|Instant messaging type of the member.
instantMessagingId|string|false|Instant messaging id of the member.
birthday|string|false|Birthday of the member.
field[ID]|string|false|A custom field belongs to the member where [ID] is the custom profile fieldid. You can replace ID with the custom field value to update the custom fields e.g. field102901.



## DeleteResponse

<a name="schemadeleteresponse"></a>

```json
{
  "status": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
status|string|false|No description



## ListMessages

<a name="schemalistmessages"></a>

```json
[
  {
    "sender": {
      "userId": 0,
      "username": "string"
    },
    "message": "string",
    "messageId": 0,
    "attachments": [
      {
        "fileName": "string",
        "URL": "string",
        "id": "string",
        "object": "string"
      }
    ],
    "dateTimestamp": 0,
    "object": "string"
  }
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[object]|false|No description
» sender|object|false|The member who created this object.
»» userId|integer|false|The userId of member who created this object.
»» username|string|false|The username of member who created this object.
» message|string|false|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
» messageId|integer|false|The unique identifier for a message.
» dateTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
» object|string|false|String representing the object’s type. Objects of the same type share the same value.
» attachments|[object]|false|No description
»» fileName|string|false|The file name of attachment.
»» URL|string|false|The attachment URL.
»» id|string|false|The unique identifier for a attachment.
»» object|string|false|String representing the object’s type. Objects of the same type share the same value.



## ListPosts

<a name="schemalistposts"></a>

```json
[
  {
    "message": "string",
    "likeCount": 0,
    "postTimestamp": 0,
    "postId": 0,
    "dislikeCount": 0,
    "author": {
      "userId": 0,
      "avatarUrl": "string",
      "username": "string"
    },
    "attachments": [
      {
        "fileName": "string",
        "URL": "string",
        "id": "string"
      }
    ],
    "attachmentCount": 0,
    "pending": true,
    "object": "string"
  }
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[object]|false|No description
» message|string|false|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
» likeCount|integer|false|Total number of post likes.
» postTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
» postId|integer|false|The unique identifier of post
» dislikeCount|integer|false|Total number of post dislikes.
» author|object|false|No description
»» userId|integer|false|The userId of member who created this object.
»» avatarUrl|string|false|The URL of an icon or image representing a particular member in forum who created this object.
»» username|string|false|The username of member who created this object.
» attachmentCount|integer|false|Total number of attachments in post.
» pending|boolean|false|Boolean representing whether a post is pending or not. Pending post will only be displayed after approval of moderator.
» object|string|false|String representing the object’s type. Objects of the same type share the same value.
» attachments|[object]|false|No description
»» fileName|string|false|The file name of attachment.
»» URL|string|false|The attachment URL.
»» id|string|false|The unique identifier for a attachment.



## AddConversation

<a name="schemaaddconversation"></a>

```json
{
  "message": "string",
  "recipientUsernames": [
    "string"
  ],
  "subject": "string",
  "senderId": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
message|string|false|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
subject|string|false|Thing that is being discussed, described for conversation.
senderId|integer|false|Sender's userId who started the conversation.
recipientUsernames|[string]|false|A list of usernames who will receive the messages.



## AddTopic

<a name="schemaaddtopic"></a>

```json
{
  "title": "string",
  "content": "string",
  "username": "string",
  "categoryId": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
title|string|true|Thing that is being discussed, described for topic.
content|string|true|Content is usually a message, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
username|string|true|The username of member to create this object.
categoryId|integer|false|The unique identifier of category to create this object.



## UpdateUser

<a name="schemaupdateuser"></a>

```json
{
  "username": "string",
  "password": "string",
  "email": "string",
  "userGroups": [],
  "signature": "string",
  "name": "string",
  "instantMessagingType": "string",
  "lastPostTimestamp": 0,
  "instantMessagingId": "string",
  "birthday": "string",
  "field[ID]": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
username|string|false|The username of member.
password|string|false|The password of member.
email|string|false|The email address of the member.
signature|string|false|Signature of member.
name|string|false|The name of member.
instantMessagingType|string|false|Instant messaging type of the member.
lastPostTimestamp|integer|false|Instant messaging type of member.
instantMessagingId|string|false|Instant messaging id of member.
birthday|string|false|Birthday of the member.
field[ID]|string|false|A custom field belongs to the member where [ID] is the custom profile fieldid. You can replace ID with the custom field value to update the custom fields e.g. field102901.



## AddMessage

<a name="schemaaddmessage"></a>

```json
{
  "message": "string",
  "userId": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
message|string|false|Message is usually a content, and its purpose is either to ask a question, answer a question or to contributes towards the forum discussion by expressing an opinion or bringing forth information.
userId|integer|false|The userId of member to create a message.



## ListConversations

<a name="schemalistconversations"></a>

```json
[
  {
    "object": "string",
    "subject": "string",
    "dateTimestamp": 0,
    "participants": [
      {
        "userId": 0,
        "avatarUrl": "string",
        "active": true,
        "username": "string",
        "unreadCount": 0,
        "isStarter": true
      }
    ],
    "conversationId": 0
  }
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[object]|false|No description
» object|string|false|String representing the object’s type. Objects of the same type share the same value.
» subject|string|false|Thing that is being discussed, described for conversation.
» dateTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
» conversationId|integer|false|The unique identifier for a conversation.
» participants|[object]|false|The list of members who participate in conversation.
»» userId|integer|false|Participant's userId.
»» avatarUrl|string|false|The URL of an icon or image representing a particular person in forum.
»» active|boolean|false|Boolean representing whether a participant is active or not.
»» username|string|false|Participant's username.
»» unreadCount|integer|false|The number of unread messages in conversation.
»» isStarter|boolean|false|Boolean representing whether a participant is started the conversation or not.



## Topic

<a name="schematopic"></a>

```json
{
  "lastPost": {
    "author": {
      "avatarUrl": "string",
      "userId": 0,
      "username": "string"
    },
    "timestamp": 0,
    "postId": 0
  },
  "viewCount": 0,
  "firstPostId": 0,
  "locked": true,
  "postCount": 0,
  "replyCount": 0,
  "pinned": true,
  "topicId": 0,
  "title": "string",
  "author": {
    "avatarUrl": "string",
    "username": "string",
    "userId": 0
  },
  "categoryId": 0,
  "dateTimestamp": 0,
  "object": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
lastPost|object|false|No description
» author|object|false|No description
»» avatarUrl|string|false|The URL of an icon or image representing a particular member in forum who created last post.
»» userId|integer|false|The userId of member who created last post.
»» username|string|false|The username of member who created last post.
» timestamp|integer|false|Time at which the last post was created. Measured in seconds since the Unix epoch.
» postId|integer|false|The unique identifier for a post.
viewCount|integer|false|The number of views in topic.
firstPostId|integer|false|The unique identifier of first post in topic.
locked|boolean|false|Boolean representing whether a topic is locked or not. Locked will prevent any new posts from being made in the topic.
postCount|integer|false|The number of posts in topic.
replyCount|integer|false|The number of replies in topic.
pinned|boolean|false|Boolean representing whether a topic is pinned or not. Pinned topic display at the beginning of that forum's topic listing to ensure that it receives attention from forum users.
topicId|integer|false|The unique identifier for a topic.
title|string|false|Thing that is being discussed, described for topic.
author|object|false|No description
» avatarUrl|string|false|The URL of an icon or image representing a particular member in forum who created this object.
» username|string|false|The username of member who created this object.
» userId|integer|false|The userId of member who created this object.
categoryId|integer|false|The unique identifier of category that belongs to this object.
dateTimestamp|integer|false|Time at which the object was created. Measured in seconds since the Unix epoch.
object|string|false|String representing the object’s type. Objects of the same type share the same value.





