# Lab 1: Hello Lambda and S3 trigger

**Tasks**
1. Create Lambda `Lambda_<PRN>` (Python) that returns `Hello from <PRN>`.
2. Create a test event, run it, show output and CloudWatch logs.
3. Create an S3 bucket, set it as trigger, upload `<PRN>.txt`, show the invocation in logs.

Background: [handler, event, context](../concepts/02-handler-event-context.md), [S3 trigger](../concepts/03-s3-trigger-and-event.md)

---

## Step 1: Create the function

Lambda > **Create function** > **Author from scratch**

| Setting | Value |
|---|---|
| Function name | `Lambda_<PRN>` |
| Runtime | Python 3.x |

Click **Create function**.

## Step 2: Return Hello

Code tab > open `lambda_function.py` > replace the code:

```python
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': 'Hello from <PRN>'
    }
```

Click **Deploy**.

## Step 3: Test

Test tab > **Create new event**

| Setting | Value |
|---|---|
| Event name | `MyTestEvent` |
| Event JSON | `{}` |

**Save** > **Test**. It shows status 200 and your message.

**Screenshot:** the test result.

## Step 4: CloudWatch logs

Monitor tab > **View CloudWatch logs** > open the latest log stream.

You see only `START`, `END`, `REPORT`. The message is missing because Lambda does not log return values. Change the code, **Deploy**, **Test** again:

```python
def lambda_handler(event, context):
    message = 'Hello from <PRN>'
    print(message)

    return {
        'statusCode': 200,
        'body': message
    }
```

Open the newest log stream. It now shows `Hello from <PRN>`.

**Screenshot:** the CloudWatch log.

## Step 5: Create the S3 bucket

S3 > **Create bucket**

| Setting | Value |
|---|---|
| Bucket name | `lambda-prn-<PRN>` (must be unique) |
| Region | Same as your Lambda |
| Other settings | Default |

## Step 6: Add the trigger

Lambda > function overview > **Add trigger**

| Setting | Value |
|---|---|
| Source | S3 |
| Bucket | your new bucket |
| Event types | All object create events |
| Prefix | blank |
| Suffix | blank |

Tick the acknowledge warning > **Add**.

## Step 7: Show S3 details in the code

Replace the code and **Deploy**:

```python
def lambda_handler(event, context):

    print("Lambda function invoked!")

    for record in event.get('Records', []):
        bucket = record['s3']['bucket']['name']
        filename = record['s3']['object']['key']

        print("Bucket:", bucket)
        print("Uploaded file:", filename)

    return {
        'statusCode': 200,
        'body': 'Hello from <PRN>'
    }
```

## Step 8: Upload and verify

1. Create a text file named `<PRN>.txt`.
2. S3 > open bucket > **Upload** > add `<PRN>.txt` > **Upload**.
3. Lambda > Monitor > View CloudWatch logs > latest log stream.

Expected:

```
Lambda function invoked!
Bucket: lambda-prn-<PRN>
Uploaded file: <PRN>.txt
```

**Screenshot:** this log.

## Cleanup

Delete the Lambda function. Empty then delete the bucket.
