---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the HundrED API!

# Authentication

Server expects for the JWT_TOKEN to be included in all API requests to the server in a header.

The header AUTHORIZATION should look like following:

`Authorization: Bearer JWT_TOKEN`

Payload should look like following: 

<code>
{
  "app_id": "APP_ID"
}
</code>


```json
{
  "app_id": "APP_ID"
}
```
> The above JSON object is should be included in JWT payload.


```shell
 curl -i -H "AUTHORIZATION: Bearer JWT_TOKEN" https://hundred.org/api/innovations/15
```
> The above command returns JSON structured like this:

```json
{  
   "innovation":{  
      "id":15,
      "title":"Third innovation",
      "cover_image_url":"fallback/collection/default5.png",
      "date":"20.6.2019",
      "body":"<p><b>What we do?</b></p> <p></p> <p><b>Why we do it?</b></p> <p></p>"
   }
}
```
<aside class="success">
You must replace <code>JWT_TOKEN</code> with generated JWT token signed with APP_SECRET and payload.
</aside>

# Innovations

## Get all innovations

```shell
curl "https://hundred.org/api/innovations"
  -H "Authorization: Bearer JWT_TOKEN"
```

> The above command returns JSON structured like this:

```json
{  
   "innovations":[  
      {  
         "id":10,
         "title":"Second innovation",
         "cover_image_url":"fallback/collection/default0.png",
         "date":"22.5.2018"
      },
      {  
         "id":5,
         "title":"First innovation",
         "cover_image_url": URL_TO_IMAGE,
         "date":"7.3.2018"
      }
   ]
}
```

This endpoint retrieves all innovations.

The request is paginated. next page you can get by passing <code>page</code> parameter.

### HTTP Request

`GET https://hundred.org/api/innovations`

### Query Parameters

Parameter | Default | Description | Options
--------- | ------- | ----------- | -----
order | featured | returns result ordered by any of the options | latest, name, views
search | empty | returns found innovations list
page | 1 | Page of the response
limit | 20 | returns exact amount of innovations up to 20

<aside class="success">
Remember — Put "Authorization: Bearer JWT_TOKEN" in header!
</aside>

## Get a specific innovation

```shell
curl "GET https://hundred.org/api/innovations/15"
  -H "Authorization: Bearer JWT_TOKEN"
```

> The above command returns JSON structured like this:

```json
{  
   "innovation":{  
      "id":15,
      "title":"Third innovation",
      "cover_image_url":"fallback/collection/default5.png",
      "date":"20.6.2019",
      "body":"<p><b>What we do?</b></p> <p></p> <p><b>Why we do it?</b></p> <p></p>"
   }
}
```

This endpoint retrieves a specific innovation.

### HTTP Request

`GET https://hundred.org/api/innovations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the innovation to retrieve
