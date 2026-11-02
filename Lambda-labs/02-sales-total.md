# Lab 2: Sales total

Upload `sales.csv` to S3. Lambda calculates total sales and saves `total_sales.csv` in the same bucket.

Background: [S3 trigger and infinite loop](../concepts/03-s3-trigger-and-event.md), [IAM](../concepts/04-iam-and-cloudwatch.md), [code explained](../concepts/05-code-explained.md)

```
Upload sales.csv --> S3 event --> Lambda --> total_sales.csv in same bucket
```

## Data

`sales.csv`

```csv
product,quantity,price
Laptop,2,60000
Mouse,5,500
Keyboard,3,1500
```

Expected `total_sales.csv`

```csv
Total_Sales
127000
```

(2 x 60000) + (5 x 500) + (3 x 1500) = 120000 + 2500 + 4500 = 127000

---

## Step 1: Create the bucket

S3 > Create bucket > name: `yourname-sales-lambda-demo-2026` (unique), same region as Lambda.

## Step 2: Create the function

Lambda > **Create function** > **Author from scratch**

| Setting | Value |
|---|---|
| Function name | `sales_total_function` |
| Runtime | Python 3.x |

**Create**. In the Code tab paste this, then **Deploy**:

```python
import json
import boto3
import csv
import io

s3 = boto3.client('s3')


def lambda_handler(event, context):

    # Get bucket and file name from event
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']

    # Avoid infinite loop if Lambda reads its own output file
    if key == "total_sales.csv":
        return

    # Read uploaded CSV file
    response = s3.get_object(Bucket=bucket, Key=key)
    lines = response['Body'].read().decode('utf-8').splitlines()

    reader = csv.DictReader(lines)

    total_sales = 0

    for row in reader:
        total_sales += int(row['quantity']) * int(row['price'])

    print("Total Sales:", total_sales)

    # Create output CSV in memory
    output = io.StringIO()
    writer = csv.writer(output)

    writer.writerow(["Total_Sales"])
    writer.writerow([total_sales])

    # Upload result file to same bucket
    s3.put_object(
        Bucket=bucket,
        Key="total_sales.csv",
        Body=output.getvalue()
    )

    return {
        "statusCode": 200,
        "total_sales": total_sales
    }
```

## Step 3: Give Lambda permission for S3

1. Function page > **Configuration** tab > **Permissions**.
2. Click the **execution role name** (opens IAM).
3. **Add permissions** > **Attach policies** > **AmazonS3FullAccess**.
4. Click **Add permissions**.

## Step 4: Configure S3 to trigger Lambda

S3 > open bucket > **Properties** > **Event notifications** > **Create event notification**

| Setting | Value |
|---|---|
| Event notification name | `sales-upload-trigger` |
| Event types | All object create events |
| Destination | Lambda function |
| Lambda function | `sales_total_function` |

**Save**.

## Step 5: Upload and check

1. Save the data above as `sales.csv` and upload it to the bucket.
2. Refresh the bucket. `total_sales.csv` should appear.
3. Open it. It should show `127000`.

If the file does not appear: Lambda > Monitor > View CloudWatch logs > open the latest log and read the error.

| Error | Cause |
|---|---|
| `AccessDenied` | Step 3 not done |
| `KeyError: 'quantity'` | Wrong CSV header |
| No log at all | Trigger missing (Step 4) or different regions |

## Cleanup

Delete the Lambda function. Empty then delete the bucket.
