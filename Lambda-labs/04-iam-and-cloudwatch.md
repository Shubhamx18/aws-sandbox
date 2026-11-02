# 4. IAM role and CloudWatch logs

## Execution role (what Lambda is allowed to do)

When you create a function, AWS creates an **execution role**. The role decides which AWS services your code may use.

The default role only allows **writing logs**. That is why `print()` works in Lab 1 with no extra setup.

Reading or writing S3 is **not** allowed by default. Without permission you get:

```
AccessDenied: User ... is not authorized to perform: s3:GetObject
```

Fix (Labs 2 and 3): Configuration > Permissions > click the role name > Add permissions > Attach policies > **AmazonS3FullAccess**.

(Real projects give only `s3:GetObject` and `s3:PutObject` for one bucket. Full access is used here for simplicity.)

## Two different permissions

| Direction | Question | How it is set |
|---|---|---|
| Lambda -> S3 | Can my code read/write the bucket? | Execution role (you attach the policy) |
| S3 -> Lambda | Can S3 start my function? | Added automatically when you create the trigger |

## CloudWatch Logs

Everything you `print()` goes to CloudWatch Logs.

- **Log group**: `/aws/lambda/<function-name>` (one per function)
- **Log stream**: a series of runs from one environment (open the latest)

Reach it from: Lambda > your function > **Monitor** > **View CloudWatch logs**.

## What a log looks like

```
START RequestId: abc-123 Version: $LATEST
Lambda function invoked!
Bucket: lambda-prn-123456
Uploaded file: 123456.txt
END RequestId: abc-123
REPORT RequestId: abc-123  Duration: 2.5 ms  Billed Duration: 3 ms  Memory Size: 128 MB  Max Memory Used: 35 MB
```

| Line | Meaning |
|---|---|
| `START` | Function began |
| your prints | Output of `print()` |
| `END` | Function finished |
| `REPORT` | Time taken, billed time, memory used |

Errors also appear here with the Python traceback. When something fails, open the latest log first.

## Tip

Logs can take a few seconds to appear. Refresh the log stream list if you do not see the newest run.
