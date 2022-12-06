# S3-utils

Helper bash scripts for file operations on an S3 bucket for my personal off-machine file storage. Uses symmetric GPG encryption on-system before upload.

## Requirements
- needs `gnupg` installed
- needs `awscli` installed 
- needs env vars configured: `S3PERSONALSTORAGEBUCKETPATH` & `S3PERSONALSTORAGECLIPROFILE`
- needs IAM policy configured for user, key/secret generated
    - ```json
        {
            "Version": "2012-10-17",
            "Statement": [
                {
                    "Sid": "AllowListInBucket",
                    "Effect": "Allow",
                    "Action": [
                        "s3:ListBucket"
                    ],
                    "Resource": [
                        "arn:aws:s3:::<bucket_name>"
                    ]
                },
                {
                    "Sid": "AllowWriteInBucket",
                    "Effect": "Allow",
                    "Action": [
                        "s3:PutObject",
                        "s3:GetObject",
                        "s3:GetObjectAttributes",
                        "s3:DeleteObject"
                    ],
                    "Resource": [
                        "arn:aws:s3:::<bucket_name>/*"
                    ]
                }
            ]
        }
        ```
