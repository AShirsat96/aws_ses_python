# AWS SES Email Sender

A Python implementation for sending emails using Amazon Simple Email Service (AWS SES). The main purpose of this python code is to send out mass marketing html emails using AWS SES service.

## Prerequisites

- Python 3.11.7
- boto3 1.34.66 (AWS SDK for Python)
- AWS Account with SES access
- AWS Access Key and Secret Access Key

## Installation

Install the required AWS SDK for Python:

```bash
pip install boto3
```

## Configuration

You'll need to configure the following AWS credentials:

```python
aws_access_key_id = <Your Access Key>
aws_secret_access_key = <Your secret access key>
myregion = <your region>
```

## Required Libraries

```python
import boto3
from botocore.exceptions import ClientError, WaiterError
import logging
```

## Usage

The main functionality is provided through the `Send_SES_Email` function. Here's a working example from the implementation:

```python
message_id = Send_SES_Email(
    aws_access_key_id,
    aws_secret_access_key,
    'ap-southeast-1',
    'test@test.com',
    ['xxxx@gmail.com', 'test@xyz.com'],
    [],  # CC addresses (empty in this example)
    [],  # BCC addresses (empty in this example)
    'Test Email Subject 5',
    'This is a test email body 5',
    'This is a test email html body 5'
)
```

### Parameters

- `aws_access`: Your AWS access key ID
- `aws_secret`: Your AWS secret access key
- `aws_region`: AWS region for SES service (e.g., 'ap-southeast-1')
- `vsource`: Sender email address
- `vTo`: List of recipient email addresses
- `vCC`: List of CC recipient email addresses
- `vBCC`: List of BCC recipient email addresses
- `vsubject`: Email subject line
- `vtext`: Plain text version of the email body
- `vhtml`: HTML version of the email body

### Return Value

The function returns a message ID if the email is sent successfully. Example of a successful message ID:
```
'010e018e039375e6-a2a37041-f498-4938-af11-9f0168b781ab-000000'
```

### Error Handling

The implementation includes error handling using try-except blocks:
- Logs successful sends with message ID and source address
- Catches and logs ClientError exceptions
- Uses Python's logging module for error tracking

## Dependencies

- boto3
- botocore.exceptions (ClientError, WaiterError)
- logging

