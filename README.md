# Email Client Library

This Python library provides a simple yet powerful interface to interact with both IMAP (Internet Message Access Protocol) and SMTP (Simple Mail Transfer Protocol) servers, facilitating email-related tasks such as retrieving and sending emails.

## Usage

### IMAP Client

#### Initialization

```python
from client import imapClient

recipient_email = "recipient@example.com"
password = "your_password"
server = "imap.example.com"
port = "587"

# Optional parameters:
use_ssl = True  # Defaults to True
move_to_archive = True  # Defaults to True

# Create an IMAP client instance
imap_client = imapClient(recipient_email, password, server, use_ssl, move_to_archive)

# Login to the IMAP server
imap_client.login()

# Perform operations...
subject_to_search = "Example Subject"
messages = imap_client.get_msg(subject_to_search)

# messages is a list of dictionaries containing message information
for msg in messages:
    print(f"Message Number: {msg['num']}")
    print(f"Subject: {msg['subject']}")
    print(f"Body: {msg['body']}")

# Move a specific message to the archive folder
message_uid_to_move = "123456789"
imap_client.move_msg(message_uid_to_move)

# Logout from the IMAP server when done
imap_client.logout()
```

### SMTP Client

#### Initialization

```python
from client import smtpClient

sender_email = "sender@example.com"
sender_password = "your_password"
smtp_server = "smtp.example.com"
smtp_port = 587

# Optional parameter:
use_ssl = True  # Defaults to True

# Create an SMTP client instance
smtp_client = smtpClient(sender_email, sender_password, smtp_server, smtp_port, use_ssl)

# Login to the SMTP server
smtp_client.login()

# Perform operations...
receiver_email = "recipient@example.com"
email_subject = "Example Subject"
email_body = "This is the body of the email."

smtp_client.send_msg(receiver_email, email_subject, email_body)

# Logout from the SMTP server when done
smtp_client.logout()
```

### Dependencies
This library uses the built-in email and smtplib modules for email-related operations.

### Note
