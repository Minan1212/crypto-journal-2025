# Week 10 – Cryptographic Attacks & Defenses

## 🔐 Topic Summary:
This week I focused on different **attacks on cryptographic systems** and the corresponding **defenses**. I learned that even the strongest algorithms can be compromised if they are used incorrectly, implemented poorly, or combined with weak human practices.

Types of attacks include brute-force, replay, man-in-the-middle (MITM), and side-channel attacks. Each has different targets—some attack the keys, others the transmission, and some exploit system timing or power usage.

Understanding these attacks helped me see that **cryptography is only one part of security**, and it's equally important to apply it properly.

---

## ⚔️ Types of Cryptographic Attacks

### 1. **Brute Force Attack**
- Tries every possible key until the correct one is found
- Works on simple or short key systems like Caesar Cipher
- 🔐 **Defense**: Use strong, long keys (e.g., 128+ bits)

### 2. **Dictionary Attack**
- Uses a precompiled list of common passwords or hash outputs
- Often used to crack password databases
- 🔐 **Defense**: Use **salted hashes**, bcrypt, or PBKDF2

### 3. **Man-in-the-Middle (MITM) Attack**
- Attacker intercepts communication between two parties
- Can modify or steal data
- 🔐 **Defense**: Use **TLS**, **public key verification**, and **certificates**

### 4. **Replay Attack**
- Resends captured valid data to trick systems
- Dangerous in payment and login systems
- 🔐 **Defense**: Use **timestamps**, **nonces**, and **session tokens**

### 5. **Side-Channel Attack**
- Observes power usage, timing, or electromagnetic leaks to infer secrets
- Doesn’t break the math, but the environment
- 🔐 **Defense**: Use **constant-time code** and secure hardware

---

## 💻 Python Code – Brute Forcing Caesar Cipher

```python
def caesar_decrypt(ciphertext, shift):
    result = ''
    for char in ciphertext:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base - shift) % 26 + base)
        else:
            result += char
    return result

# Brute force Caesar cipher
ciphertext = "KHOOR"
for shift in range(1, 26):
    print(f"Shift {shift}: {caesar_decrypt(ciphertext, shift)}")
This simple script shows how Caesar Cipher can be easily broken with brute force—trying all possible shifts.

🛡 Defenses Summary Table
Attack Type	Defense
Brute Force	Use strong keys (e.g., AES-256)
Dictionary	Salt + hash passwords (e.g., bcrypt)
MITM	TLS, certificate validation
Replay	Nonces, timestamps, session IDs
Side-Channel	Hardware shielding, constant-time code
💡 Reflection
Before this week, I thought using encryption was enough. But now I understand that attackers often target the implementation, not just the algorithm.

The MITM attack example really made me think about how attackers can slip into a conversation without breaking the encryption if there’s no authentication. I also learned how brute-force attacks can still succeed on weak ciphers, which is why modern systems use long, complex keys.

This week helped me realize that secure cryptographic systems are about how you use the tools, not just which tools you use.

🔗 Resources Consulted
Crypto101 – Attacks and Defenses

OWASP – Cryptographic Failures

YouTube – Brute Force and MITM Attacks Explained
