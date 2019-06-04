# REST

## Create

Create a new resource:

```txt
POST  /user/posts
```

## Read

Retrieve a collection of resources:

```txt
GET  /user/posts
```

Retrieve a known resource:

```txt
GET  /user/posts/1
```

Retrieve a filtered collection of resources:

```txt
GET  /user/posts?author=jdoe
```

## Update

Update a known resource:

```txt
PUT  /user/posts/1
```

Partially update a known resource:

```txt
PATCH  /user/posts/1
```

## Delete

Delete a known resource:

```txt
DELETE  /user/posts/1
```

## Links

- [Representational state transfer](https://en.wikipedia.org/wiki/Representational_state_transfer)
- [REST API Tutorial](https://restfulapi.net)
- [PUT vs. POST in REST](https://stackoverflow.com/q/630453)
- [What are the best/common RESTful url verbs and actions?](https://stackoverflow.com/q/256349)
