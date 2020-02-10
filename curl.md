# [cURL](https://curl.haxx.se/)

Do a POST request with JSON data:

```bash
curl --location --request POST --header 'Content-Type: application/json' --data '{"foo":"bar"}' 'https://example.org/api/'
```

Do a POST request with form data:

```bash
curl --location --request POST --header 'Content-Type: application/x-www-form-urlencoded' --data 'foo1=bar1&foo2=bar2' 'https://example.org/api/'
```

Do a GET request with query string parameters:

```bash
curl --location --request GET 'https://example.org/api/?foo1=bar1&foo2=bar2'
```
