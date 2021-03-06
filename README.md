# boilerplate-restify-for-rest-api [![Build Status][travis-image]][travis-url] [![Dependency Status][depstat-image]][depstat-url] [![License: MIT][license-image]][license-url]

Boilerplate of Restify for REST API

## Required

- Docker installed

## Let's begin developing

```bash
git clone https://github.com/keidrun/boilerplate-restify-for-rest-api.git
cd boilerplate-restify-for-rest-api
docker-compose up
```

## Develop with testing

```bash
docker-compose up -d
docker exec -it my_app yarn test-watch
```

## API endpoints

|  Method  |     URI      |         Data          |
| -------- | ------------ | --------------------- |
|   POST   |  /users      | name,age,gender,email |
|   GET    |  /users      |           -           |
|   GET    |  /users/:id  |           -           |
|   PUT    |  /users/:id  | name,age,gender,email |
|  DELETE  |  /users/:id  |           -           |

## Manual Tests

```bash
$ curl -v -H "Accept:application/json" -H "Content-Type:application/json" -X POST -d '{"name":"Keid","age":30,"gender":"male","email":"keid@example.com"}' http://localhost:3000/users | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": {
    "_id": "5bb30edcd1b036e33f6a2e57",
    "name": "Keid",
    "age": 30,
    "gender": "male",
    "email": "keid@example.com",
    "__v": 0
  }
}
$ curl -v -H "Accept:application/json" -H "Content-Type:application/json" -X POST -d '{"name":"Tom","age":24,"gender":"male","email":"tom@example.com"}' http://localhost:3000/users | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": {
    "_id": "5bb30f70d1b036e33f6a2e58",
    "name": "Tom",
    "age": 24,
    "gender": "male",
    "email": "tom@example.com",
    "__v": 0
  }
}
$ curl -v -H "Accept:application/json" -H "Content-Type:application/json" -X POST -d '{"name":"Mary","age":32,"gender":"female","email":"mary@example.com"}' http://localhost:3000/users | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": {
    "_id": "5bb30f84d1b036e33f6a2e59",
    "name": "Mary",
    "age": 32,
    "gender": "female",
    "email": "mary@example.com",
    "__v": 0
  }
}
$ curl -v -H "Accept:application/json" http://localhost:3000/users | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": [
    {
      "_id": "5bb30edcd1b036e33f6a2e57",
      "name": "Keid",
      "age": 30,
      "gender": "male",
      "email": "keid@example.com",
      "__v": 0
    },
    {
      "_id": "5bb30f70d1b036e33f6a2e58",
      "name": "Tom",
      "age": 24,
      "gender": "male",
      "email": "tom@example.com",
      "__v": 0
    },
    {
      "_id": "5bb30f84d1b036e33f6a2e59",
      "name": "Mary",
      "age": 32,
      "gender": "female",
      "email": "mary@example.com",
      "__v": 0
    }
  ]
}
$ curl -v -H "Accept:application/json" http://localhost:3000/users/5bb30f70d1b036e33f6a2e58 | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": {
    "_id": "5bb30f70d1b036e33f6a2e58",
    "name": "Tom",
    "age": 24,
    "gender": "male",
    "email": "tom@example.com",
    "__v": 0
  }
}
$ curl -v -H "Accept:application/json" -H "Content-Type:application/json" -X PUT -d '{"name":"Amily","age":21,"gender":"female","email":"amily@example.com"}' http://localhost:3000/users/5bb30f70d1b036e33f6a2e58 | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": {
    "_id": "5bb30f70d1b036e33f6a2e58",
    "name": "Amily",
    "age": 21,
    "gender": "female",
    "email": "amily@example.com",
    "__v": 0
  }
}
$ curl -v -H "Accept:application/json" -X DELETE http://localhost:3000/users/5bb30f84d1b036e33f6a2e59 | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": {
    "_id": "5bb30f84d1b036e33f6a2e59",
    "name": "Mary",
    "age": 32,
    "gender": "female",
    "email": "mary@example.com",
    "__v": 0
  }
}
$ curl -v -H "Accept:application/json" http://localhost:3000/users | jq
...
< HTTP/1.1 200 OK
...
{
  "status": "success",
  "data": [
    {
      "_id": "5bb30edcd1b036e33f6a2e57",
      "name": "Keid",
      "age": 30,
      "gender": "male",
      "email": "keid@example.com",
      "__v": 0
    },
    {
      "_id": "5bb30f70d1b036e33f6a2e58",
      "name": "Amily",
      "age": 21,
      "gender": "female",
      "email": "amily@example.com",
      "__v": 0
    }
  ]
}
```

[travis-url]: https://travis-ci.org/keidrun/boilerplate-restify-for-rest-api
[travis-image]: https://secure.travis-ci.org/keidrun/boilerplate-restify-for-rest-api.svg?branch=master
[depstat-url]: https://david-dm.org/keidrun/boilerplate-restify-for-rest-api
[depstat-image]: https://david-dm.org/keidrun/boilerplate-restify-for-rest-api.svg
[license-url]: https://opensource.org/licenses/MIT
[license-image]: https://img.shields.io/badge/License-MIT-yellow.svg
