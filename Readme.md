Public repo for smartcountry.group
=======

Api reference
=======

Firstly you need get API KEY from your smartcountry.group account profile.

Request url format is https://api.smartcountry.group/?key=[YOUR_API_KEY]. Use http POST request with JSON body.

Request JSON message format:

```
{"method":"[METHOD_NAME]"}
```
All methods descriptions are below

Response JSON format

```
{
  "result": true,
  "data": {
     [RESPONSE_DATA_OBJECT]
  }
}
```
