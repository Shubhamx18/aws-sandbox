# Exercise: Student marks

3 students, 3 subjects. Upload `marks.csv` to S3. Lambda saves **total** and **average** marks per student in `result.csv` in the same bucket.

Background: [code explained](../concepts/05-code-explained.md) (see "Group marks by student")

## Data

`marks.csv` (no header row)

```csv
Alice,Python,75
Alice,Linux,60
Alice,Cloud,68
Bob,Python,55
Bob,Linux,70
Bob,Cloud,82
Charlie,Python,49
Charlie,Linux,69
Charlie,Cloud,71
```

Expected `result.csv`

```csv
Student,Total_Marks,Average_Marks
Alice,203,67.67
Bob,207,69.0
Charlie,189,63.0
```

---

## Step 1: Create the bucket

`yourname-marks-lambda-2026` (unique), same region as Lambda.

## Step 2: Create the function

| Setting | Value |
|---|---|
| Function name | `marks_result_function` |
| Runtime | Python 3.x |

Paste in the Code tab and **Deploy**:

```python
import boto3
import csv
import io
from collections import defaultdict

s3 = boto3.client('s3')


def lambda_handler(event, context):

    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']

    # Only process marks.csv (also stops the infinite loop on result.csv)
    if key != "marks.csv":
        print("Skipping file:", key)
        return

    # Read marks.csv
    response = s3.get_object(Bucket=bucket, Key=key)
    lines = response['Body'].read().decode('utf-8').splitlines()

    # Group marks by student
    marks = defaultdict(list)

    for row in csv.reader(lines):
        if len(row) < 3:
            continue
        student = row[0].strip()
        score = int(row[2])
        marks[student].append(score)

    # Build result.csv in memory
    output = io.StringIO()
    writer = csv.writer(output)
    writer.writerow(["Student", "Total_Marks", "Average_Marks"])

    for student, scores in marks.items():
        total = sum(scores)
        average = round(total / len(scores), 2)
        print(student, total, average)
        writer.writerow([student, total, average])

    # Save result.csv in the same bucket
    s3.put_object(
        Bucket=bucket,
        Key="result.csv",
        Body=output.getvalue()
    )

    return {"statusCode": 200, "body": "result.csv created"}
```

## Step 3: Give Lambda permission for S3

Configuration > Permissions > click the execution role name > Add permissions > Attach policies > **AmazonS3FullAccess** > Add permissions.

## Step 4: Add the S3 trigger

S3 > bucket > Properties > Event notifications > Create event notification

| Setting | Value |
|---|---|
| Name | `marks-upload-trigger` |
| Event types | All object create events |
| Destination | Lambda function > `marks_result_function` |

Save.

## Step 5: Upload and verify

1. Save the data as `marks.csv` and upload it to the bucket.
2. `result.csv` should appear. Open it and compare with the expected output.
3. If missing: Lambda > Monitor > View CloudWatch logs.

The file must be named exactly `marks.csv`, because the code ignores every other file name.

## Cleanup

Delete the Lambda function. Empty then delete the bucket.
