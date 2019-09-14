---
layout: post
title:  "Basics of Digital Security"
date:   2019-03-15 13:55:23 +0530
categories: DigitalSecurity
---

# Basics of Digital Security
For all software developers, some basic knowledge of digital security is absolutely important although they may not be digital security experts. So in this blog, I will be discussing some basic concepts of digital security. 

## Hashing and Encryption 
There seems to be some confusion between hashing and encryption so let us start with that.
Hashing is a process in which a string is hashed and an __irreversible output__ is generated. It can also happen that multiple strings can give the same hashed output. But the important thing to keep in mind about hashing is that the hashed output is completely irreversible which means that it is never possible to get back the original input from the hashed output.
The basic hashing algirithm is MD5. But the more advanced hashing algorithms include SHA-1, SHA-256, SHA-384 , SHA-512 etc. And all these can be further enhanced by adding a salt.
One of the most advanced hashing algorithm is __PBKDF2WithHmacSHA1__
Please please also refer to my Github project [DigitalSecurityExamples](https://github.com/msoumik78/DigitalSecurityExamples/blob/master/src/org/experiments/HashingDemonstrations.java)

Some sample output from the program:
Input content: I am Soumik, Hashing Algo: MD5, Salted: true, HashedHexOutput: ed23310e138b761133e398eeb5ec9227
Input content: I am Soumik, Hashing Algo: SHA-256, Salted: true, HashedHexOutput: e11decdd1856ab9549deac17dc98c6bee790d8d1c7c70b7d8d5a2621a734e5be

On the other hand, encryption is a technique in which a string is transformed to a completely different one but the process is reversible. Also another difference with encryption is that no 2 strings can produce the same encrypted output.
Normally encryption is done using some keys and hence there are 2 types of encryption methodologies:
* Symmetric encryption - This is the basic type in which encryption and decryption are both acheived using the same key. Downside of this approach is that the same key has to be shared between the sender and the receiver and hence it can be stolen. Example of this is __AES__ encryption. 
Please please also refer to my Github project [DigitalSecurityExamples](https://github.com/msoumik78/DigitalSecurityExamples/blob/master/src/org/experiments/SymmetricEncryptionDemonstration.java)
* Assymetric encryption - This is the more advanced and the industry standard approach in which encryption and decryption are done by a key-pair or the so called "Public-Private key pair." So the sender of the message will encrypt the message with the public key of the receiver, so that it is only the receiver (who has his own private key) can de-crypt it and nobody else can.
So it is safe against "man in the middle attack".
Please please also refer to my Github project [DigitalSecurityExamples](https://github.com/msoumik78/DigitalSecurityExamples/blob/master/src/org/experiments/AsymmetricEncryptionDemonstration.java)

## When to use hashing and when to use encryption ?
Hashing is used typically for storing important credentials like passwords which do not need to be seen. So normally an application would store the hash of an user's password in the database, and during the authentication process - the user provided password is hashed and compared to the stored hashed password.

However encryption is used to transfer secret/ confidential information over the wire. So typically confidential information (but which need to be seen/read) is encrypted with the receiver's public
key and sent over the wire. Only the receiver (who has his own private key) can de-crypt the message and nobody else can.

## Digital Signature vs Digital Signing
