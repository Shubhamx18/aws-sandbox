# 3. How S3 triggers Lambda

## Flow

```
Upload file --> S3 bucket --> event notification --> Lambda runs with event --> your code
```

You set this up once (Add trigger, or bucket > Properties > Event notifications). After that, every matching upload starts Lambda automatically.

## The event S3 sends

When you upload `sales.csv` to bucket `my-bucket`, Lambda receives (shortened):

```json
{
  "Records": [
    {
      "eventName": "ObjectCreated:Put",
      "s3": {
        "bucket": { "name": "my-bucket" },
        "object": { "key": "sales.csv", "size": 62 }
      }
    }
  ]
}
```

## Reading it in Python

| Code | Result |
|---|---|
| `event['Records']` | list of records |
| `event['Records'][0]` | first record |
| `...['s3']['bucket']['name']` | `my-bucket` |
| `...['s3']['object']['key']` | `sales.csv` |

`key` means the **file name** (including folder path, like `data/sales.csv`).

## `[0]` vs a `for` loop

- `event['Records'][0]` takes only the first record. Fine for these labs (one file at a time).
- `for record in event['Records']:` handles every record. Safer in general. Lab 1 uses this.

## The infinite loop problem

In Labs 2 and 3, Lambda **writes a new file into the same bucket** it is triggered by:

```
Upload sales.csv --> Lambda --> writes total_sales.csv --> S3 sees a new file --> Lambda again --> writes again --> ...
```

This repeats forever and costs money. Fix it inside the code by ignoring your own output file:

```python
if key == "total_sales.csv":
    return
```

Other fixes: use a different bucket for output, or set the trigger Prefix/Suffix (for example only `.csv` files in `input/`).

## Rules to remember

- S3 bucket and Lambda must be in the **same region**.
- Event type **All object create events** means upload, copy and multipart upload all trigger Lambda.
- S3 calls Lambda **asynchronously**: S3 does not wait for the result. If the function errors, Lambda retries 2 more times.
- File names with spaces or special characters arrive URL-encoded (`my file.csv` becomes `my+file.csv`). Decode with:

```python
from urllib.parse import unquote_plus
key = unquote_plus(key)
```
