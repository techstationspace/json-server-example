# What is json-server

Is a super simple package that allow you to quickly prototype a JSON API.

[Json-server DOC](https://github.com/typicode/json-server#getting-started)

Your DB is a JSON file. 

```js
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

All the the first level keys of your JSON are exposed as resources on a specific path:

```
  http://localhost:3000/posts
  http://localhost:3000/comments
  http://localhost:3000/profile
```

If add a key (ex: "pizzas" )


```js
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

a new route is added:

```
  http://localhost:3000/posts
  http://localhost:3000/comments
  http://localhost:3000/profile
  http://localhost:3000/pizzas
```


# Play with Curl

curl -d "@post2.json" -X POST http://localhost:3000/posts


curl -d "@post3.json" -H "Content-Type: application/json" -X POST http://localhost:3000/posts

-H "Content-Type: application/json"

curl -d "title=value1&author=value2" -H "Content-Type: application/x-www-form-urlencoded"  -X POST http://localhost:3000/posts


