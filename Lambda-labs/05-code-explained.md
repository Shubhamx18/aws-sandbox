# 5. The Python code explained (boto3 and CSV)

## boto3

`boto3` is the AWS library for Python. It is already available inside Lambda.

```python
import boto3
s3 = boto3.client('s3')
```

Create the client **outside** the handler so Lambda can reuse it across runs.

## Read a file from S3

```python
response = s3.get_object(Bucket=bucket, Key=key)
lines = response['Body'].read().decode('utf-8').splitlines()
```

| Part | Meaning |
|---|---|
| `get_object` | Download the file |
| `response['Body']` | File content as a stream |
| `.read()` | Read all bytes |
| `.decode('utf-8')` | Bytes to text |
| `.splitlines()` | Text to a list of lines |

Result for `sales.csv`:

```python
['product,quantity,price', 'Laptop,2,60000', 'Mouse,5,500', 'Keyboard,3,1500']
```

## Parse CSV

**`csv.DictReader`**: uses the first line as column names. Each row becomes a dictionary.

```python
reader = csv.DictReader(lines)
for row in reader:
    # row = {'product': 'Laptop', 'quantity': '2', 'price': '60000'}
    total += int(row['quantity']) * int(row['price'])
```

CSV values are always **text**, so convert with `int()` before calculating.

**`csv.reader`**: no header, each row is a list. Used for `marks.csv` (no header row).

```python
for row in csv.reader(lines):
    # row = ['Alice', 'Python', '75']
```

## Write a file to S3

Build the CSV text in memory, then upload:

```python
output = io.StringIO()          # a fake file in memory
writer = csv.writer(output)
writer.writerow(["Total_Sales"])
writer.writerow([total_sales])

s3.put_object(Bucket=bucket, Key="total_sales.csv", Body=output.getvalue())
```

`output.getvalue()` returns everything written so far as one string. No local file is needed.

## Group marks by student (Lab 3)

```python
from collections import defaultdict
marks = defaultdict(list)

marks['Alice'].append(75)
marks['Alice'].append(60)
# marks = {'Alice': [75, 60]}
```

`defaultdict(list)` creates an empty list automatically the first time a name appears, so no "does the key exist" check is needed.

Then:

```python
total = sum(scores)
average = round(total / len(scores), 2)
```

## Why `return` at the top for our own file

```python
if key == "total_sales.csv":
    return
```

Stops the infinite loop (see concept 3).
