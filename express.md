# [Express](https://expressjs.com/)

Return response as HTML:

```js
response.send('HTML <br> here');
```

Return response as JSON:

```js
response.json({foo: 'bar'});
// or
response.send({foo: 'bar'});
```

Return error response with a JSON payload:

```js
response
  .status(500)
  .json({
    error: 'message'
  });
```

Return an empty response (i.e. no response body):

```js
response
  .status(401)
  .end();
```
