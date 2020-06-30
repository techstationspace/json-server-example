# What is json-server

Is a super simple package that allow you to quickly prototype a JSON API.

[Json-server DOC](https://github.com/typicode/json-server#getting-started)

Install JSON Server

```
npm install -g json-server
```

Your DB is a JSON file. 

```json
{
  "posts": [
    {
      "id": 1,
      "title": "json-server",
      "author": "typicode"
    }
  ],
  "comments": [
    {
      "id": 1,
      "body": "some comment",
      "postId": 1
    }
  ],
  "profile": {
    "name": "typicode"
  }
}
```

Start JSON Server

```bash
json-server --watch db.json
```


All the first level keys of your JSON are exposed as resources on a specific path:

```
  http://localhost:3000/posts
  http://localhost:3000/comments
  http://localhost:3000/profile
```

If you add a key (ex: "pizzas" ):


```json
{
  "posts": [
    {
      "id": 1,
      "title": "json-server",
      "author": "typicode"
    }
  ],
  "comments": [
    {
      "id": 1,
      "body": "some comment",
      "postId": 1
    }
  ],
  "profile": {
    "name": "typicode"
  },
  "pizzas": [
    {
      "name": "Peperoni e Salsiccia"
    }
  ]
}
```

a new route is added ("http://localhost:3000/pizzas"):

```
  http://localhost:3000/posts
  http://localhost:3000/comments
  http://localhost:3000/profile
  http://localhost:3000/pizzas
```


Also when doing requests, it's good to know that:

- If you make POST, PUT, PATCH or DELETE requests, changes will be automatically and safely saved to `db.json` using [lowdb](https://github.com/typicode/lowdb).
- Your request body JSON should be object enclosed, just like the GET output. (for example `{"name": "Foobar"}`)
- Id values are not mutable. Any `id` value in the body of your PUT or PATCH request will be ignored. Only a value set in a POST request will be respected, but only if not already taken.
- A POST, PUT or PATCH request should include a `Content-Type: application/json` header to use the JSON in the request body. Otherwise it will return a 2XX status code, but without changes being made to the data.

# Play with Curl

## POST
curl -v -d "@post3.json" -H "Content-Type: application/json" -X POST http://localhost:3000/posts


curl -v -d "title=value1&author=value2" -H "Content-Type: application/x-www-form-urlencoded"  -X POST http://localhost:3000/posts


curl -v -d "@post2.json" -X POST http://localhost:3000/posts

## PUT

If the post with id 3 exists, the code below will update it:

```bash
curl -v -d "@put3.json" -H "Content-Type: application/json" -X PUT http://localhost:3000/posts/3
```

More about CURL: https://gist.github.com/subfuzion/08c5d85437d5d4f00e58
