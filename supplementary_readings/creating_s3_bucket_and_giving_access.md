
Best video to creat bucket, user and policies for accessing it.
https://www.youtube.com/watch?v=ACmQGfCzjkc

This is how final policy looks like

```json
{
  "Effect": "Allow",
  "Action": [
    "s3:GetObject",
    "s3:PutObject",
    "s3:DeleteObject"
  ],
  "Resource": "arn:aws:s3:::ragproject001/*"
}

```

# remove my bucket name and make it generic
