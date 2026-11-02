# 2. Handler, event and context

Every Python Lambda function has this shape:

```python
def lambda_handler(event, context):
    return {'statusCode': 200, 'body': 'Hello'}
```

## Handler

The **handler** is the function Lambda calls first. Its location is set in Runtime settings as:

```
lambda_function.lambda_handler
   |                 |
 file name        function name
 (lambda_function.py)
```

If you rename the file or function, you must change this setting, or Lambda fails with "handler not found".

## event

The input data. It is a Python dictionary built from JSON.

- **S3 trigger**: event describes the uploaded file (bucket name, file name).
- **Test button**: event is whatever JSON you typed in the test event (`{}` means empty dictionary).

The function reads what it needs from `event`:

```python
bucket = event['Records'][0]['s3']['bucket']['name']
```

## context

Information about the running function. You rarely need it.

```python
context.function_name                 # Lambda_<PRN>
context.aws_request_id                # unique id of this run
context.get_remaining_time_in_millis()  # time left before timeout
```

## Return value vs print

| | Where it goes |
|---|---|
| `return {...}` | Shown in the **Test** result. With an S3 trigger, the return value is ignored |
| `print(...)` | Written to **CloudWatch Logs** |

This is why the Hello message did not appear in CloudWatch in Lab 1 at first: it was only returned, not printed. Add `print()` to see it in logs.

## The return dictionary

```python
{'statusCode': 200, 'body': 'Hello from <PRN>'}
```

`statusCode` and `body` are the format used for web (API) responses. Here it is just a convention. 200 means success.

## Deploy vs Test

- **Deploy**: saves your code so Lambda uses it. If you skip this, the old code runs.
- **Test**: runs the deployed code with your test event.

Always: edit code, **Deploy**, then Test.
