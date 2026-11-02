# 1. What is Lambda

AWS Lambda runs your code **only when something happens**. You do not create or manage a server.

You give Lambda:
- your code (a Python function)
- a trigger (what should start it, for example a file upload to S3)

Lambda does the rest: starts a machine, runs the function, stops.

## Normal server vs Lambda

| | Server (EC2) | Lambda |
|---|---|---|
| Runs | 24/7 | Only when triggered |
| You manage | OS, updates, scaling | Only your code |
| You pay for | Every hour it is on | Only the time your code runs |
| Scaling | You set it up | Automatic (10 uploads = 10 runs in parallel) |

## Life of one run

```
Event happens (file uploaded)
        |
        v
Lambda starts an environment (first time = "cold start", a small delay)
        |
        v
Your function runs with the event data
        |
        v
Function finishes -> result returned -> logs go to CloudWatch
```

Lambda may keep the environment alive for a short time and reuse it for the next event.

## Important rules

- **Stateless**: Lambda does not remember anything between runs. Store data in S3 or a database, not in variables.
- **Time limit**: default timeout is 3 seconds, maximum is 15 minutes (change under Configuration > General configuration).
- **Memory**: default 128 MB, adjustable.
- **Storage**: files saved inside Lambda are temporary (`/tmp` only). Save permanent results to S3.

## Where it fits in these labs

```
You upload a file --> S3 --> triggers --> Lambda --> reads/writes S3, prints to CloudWatch
```
