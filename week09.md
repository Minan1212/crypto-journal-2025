# Week 09 – Cryptography in the Real World

## 🔐 Topic Summary:
This week I explored how cryptography is used in **real-world systems and applications**. I already knew about basic ciphers and key exchanges, but this week tied it all together and showed me how encryption works in:

- 💻 Secure web browsing (HTTPS)
- 📱 Messaging apps (Signal, WhatsApp)
- 🏦 Online banking and e-commerce
- 💾 Data-at-rest (encrypted files, drives)
- 🔐 Blockchain and cryptocurrencies

These systems use combinations of **symmetric encryption**, **asymmetric encryption**, **digital signatures**, **hashing**, and **key management** — often layered in complex protocols like **TLS**, **PGP**, and **SSL**.

---

## 🌐 Examples of Cryptography in Action

### 1. HTTPS & TLS (SSL):
- When I access `https://example.com`, my browser:
  - Verifies the site's **digital certificate**
  - Exchanges a **session key** securely using **Diffie-Hellman** or **RSA**
  - All communication is then encrypted with **AES** (symmetric encryption)

### 2. Secure Messaging (Signal Protocol):
- Uses **Double Ratchet Algorithm** combining:
  - Diffie-Hellman key exchange
  - AES for message encryption
  - SHA-256 for message authentication
- Supports **forward secrecy** and **message-level encryption**

### 3. Cryptocurrency (e.g., Bitcoin):
- Uses **digital signatures** (ECDSA) to sign transactions
- Hashing (SHA-256) secures blocks and links them together
- Asymmetric cryptography ensures only the private key owner can spend funds

---

## 💻 Python Practice – Encrypting and Decrypting a File (using Fernet)

> 🔧 Requires `cryptography` package:  
> `pip install cryptography`

```python
from cryptography.fernet import Fernet

# Generate a key and save it
key = Fernet.generate_key()
cipher = Fernet(key)

# Message
plaintext = b"Top secret document!"
ciphertext = cipher.encrypt(plaintext)

# Decryption
decrypted = cipher.decrypt(ciphertext)

print("Encrypted:", ciphertext)
print("Decrypted:", decrypted)
This simulates file encryption, showing how easily cryptography can be applied with libraries like Fernet (which uses AES internally).

⚠️ Challenges in the Real World
Key Management: Protecting and storing keys securely is critical.

User Behavior: Weak passwords and social engineering can bypass crypto.

Backdoors & Malware: Even strong cryptography can be undermined by compromised devices.

Performance Trade-offs: Strong encryption = more CPU, slower speed

🔁 Real-World Crypto Comparison Table
System	Crypto Used	Purpose	Tech Stack
HTTPS	RSA, DH, AES, SHA-256	Web encryption	TLS, X.509, CA certs
Signal Messenger	AES, DH, SHA-256	End-to-end encryption	Signal protocol
Bitcoin	ECDSA, SHA-256	Transaction verification	Blockchain
FileVault/BitLocker	AES	Disk encryption	OS-Level Full Disk
💡 Reflection
This week was eye-opening because it showed how all the cryptographic concepts I’ve learned come together in real-world applications. I now understand how websites, banking, messaging, and blockchain systems protect data using encryption, key exchange, and signatures.

I also learned that perfect math doesn’t mean perfect security — if the keys are stolen, or if users are tricked, encryption fails. Security is about the whole system, not just the algorithm.

Seeing how real tools like OpenSSL and Fernet are used made me more confident about applying cryptography in my own coding projects in the future.

🔗 Resources Consulted
Crypto101 – Real-World Applications

cryptography.io – Python Encryption

YouTube – HTTPS, TLS, and Cryptography
