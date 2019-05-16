---
Date: 2019/04/18
Source: https://learn.zybooks.com/zybook/WGUC9602018/chapter/2/section/20
---

# Module 8 - Mathematical Foundations of Encryption

## 2.21 - Introduction to Cryptography

Important terms:

**Encrypt**: the process of transforming information or data into a code to prevent unauthorized access.  
**Decrypt**: the process of transforming data that has been rendered unreadable through encryption back to its unencrypted form.  
**Cyphertext**: an encrypted message.  
**Plaintext**: an unencrypted message.  
**Key**: an unpredictable (typically large and random) string of numbers to decrypt an encrypted message.

---

## 2.22 - Encryption and Decryption

**Symmetric Key Cryptosystem** - Uses the same key to decrypt and encrypt the message.

|                       **Encrypt**                       |     **Decrypt**      |
| :-----------------------------------------------------: | :------------------: |
|                  $c = (m + k) \mod N$                   | $m = (c - k) \mod N$ |
| m = message<br>k = key 1<br>N = key 2<br>c = cyphertext |

---

## 2.23 - RSA Encryption

RSA encryption uses a public key for encryption and a private key for decryption. It's based on very large numbers (hundreds of digits)

**Preparation of public and private keys in RSA**

1. Bob selects two large prime numbers, p and q
2. Bob computes N = pq and φ = (p-1)(q-1)
3. Bob finds an integer e such that gcd(e, φ) = 1
4. Bob computes the multiplicative inverse of e mod φ: an integer d such that (ed mod φ) = 1
5. Public (encryption) key: N and e
6. Private (decryption) key: d

![7.3](./Img/7.3.JPG)

## 2.24 - RSA Decryption

![7.4](./Img/7.4.JPG)
