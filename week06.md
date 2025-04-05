# Week 06 – Digital Signatures & Integrity

## 🔐 Topic Summary:
This week I learned about **Digital Signatures**, which are used to verify the **authenticity** and **integrity** of messages.

They are based on **asymmetric cryptography**:
- The sender **signs** the message using their **private key**
- The receiver **verifies** it using the **sender’s public key**

Digital signatures also use **hash functions** (like SHA-256) to compress data into a digest before signing.  
If even a small change is made to the message, the signature will no longer be valid.

Common uses include:
- Software updates
- Digital certificates (SSL)
- Secure emails
- Blockchain transactions

---

## 🔄 Manual Understanding – Digital Signature Process

### Steps:
1. Sender creates a message: `"Send $100 to Bob"`
2. Sender hashes the message with **SHA-256**
3. Sender encrypts the hash with **their private key** (this is the signature)
4. Sender sends both the **message and the signature**
5. Receiver:
   - Hashes the message
   - Decrypts the signature using **sender's public key**
   - Compares both digests  
   ✅ If they match → Signature is valid

If the message or signature is altered, verification will fail. ❌

---

## 💻 Python Code – Digital Signature (RSA + SHA-256)

> 🔧 Make sure to install PyCryptodome:  
> `pip install pycryptodome`

```python
from Crypto.PublicKey import RSA
from Crypto.Signature import pkcs1_15
from Crypto.Hash import SHA256

# Generate key pair
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Message
message = b"Send $100 to Bob"

# Create hash of message
hash_msg = SHA256.new(message)

# Sign the message
signature = pkcs1_15.new(private_key).sign(hash_msg)

# Verify the signature
try:
    pkcs1_15.new(public_key).verify(hash_msg, signature)
    print("✅ Signature is valid.")
except (ValueError, TypeError):
    print("❌ Signature is invalid.")
This example shows how to digitally sign a message and verify it using RSA and SHA-256.

⚔️ Attacks and Considerations
Key Theft: If private key is stolen, anyone can forge signatures.

Replay Attacks: Attackers can reuse old valid messages unless timestamps or nonces are added.

Hash Collisions: Using weak hashes (like MD5) can lead to forged signatures.

Best Practices:
Use SHA-256 or stronger

Use 2048-bit keys or more

Keep private keys secure

🔁 Comparison Table
Method	Key Type	Integrity	Authentication	Non-repudiation	Common Use
Hash Only	None	✅ Yes	❌ No	❌ No	File verification
HMAC	Symmetric Key	✅ Yes	✅ Yes	❌ No	API tokens
Digital Signature	Asymmetric Key	✅ Yes	✅ Yes	✅ Yes	Emails, Blockchain, SSL
💡 Reflection:
This week taught me that digital signatures don’t hide data — they prove identity and integrity.

I always thought encryption and signing were the same, but now I understand they serve different purposes. Encryption hides content, while signing ensures that the message is authentic and hasn’t been tampered with.

The Python code helped me visualize the process clearly, and I now understand why digital signatures are so important in modern security systems like blockchain, emails, and certificates.

🔗 Resources Consulted
Crypto101 – Digital Signatures

PyCryptodome Docs – RSA Signing

YouTube – What is a Digital Signature?
