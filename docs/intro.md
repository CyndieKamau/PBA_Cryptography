# Cryptography

## Introduction to Cryptography

Cryptography is the art and science of keeping secrets.

A secret is data you know that no one else knows.

Here's the current cryptography landscape:

![Cryptography Landscape](../../pba-docs/static/img/landscape.png)


## What are the cryptographic guarantees?

### Data Authenticity:

Data Authenticity is, example, verifying that the letter you received really comes from the person it claims to be from.

Digital signatures help ensure messages really come from the stated person, and are hard to fake.

### Data Integrity:

Data Integrity is now checking if the letter you received has been tampered with during delivery, example the seal has been opened.

### Non Repudiation

In non repudiation, once the letter is sent, the sender of the message cannot deny that they sent the letter. 

### Data Confidentiality:

Only someone who knows a secret (eg the password to access the letter) will access the private letter's contents.

N.B Confidentiality in communication channels like when Alice and Bob send secret messages, involves two sub types:
- **Forward Secrecy:** If someone learns Alice's secret key, they still can't read her future messages after a certain point.
- **Backward Secrecy:** If someone finds out Alice's secret key, they can't read her past messages that were sent before a certain time.

N.B!! Cryptography does not guarantee **Data Availability:** Data is available to people 24 7.
