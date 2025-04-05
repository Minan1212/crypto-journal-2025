# Week 11 – Emerging Cryptographic Technologies

## 🔐 Topic Summary:
This week focused on **emerging cryptographic technologies** — especially **post-quantum cryptography**, **homomorphic encryption**, and **zero-knowledge proofs (ZKPs)**.

As computing power increases, especially with the rise of **quantum computers**, existing cryptographic systems like RSA and ECC could become breakable. This week introduced new systems designed to resist quantum attacks.

Emerging cryptography aims to:
- Stay secure in the **post-quantum era**
- Allow computations on **encrypted data** (privacy-preserving)
- Enable **authentication without revealing secrets**

---

## 🌱 Technologies I Explored

### 1. 🧠 Post-Quantum Cryptography (PQC)
- Designed to be secure against quantum computers
- Uses **lattice-based**, **code-based**, and **multivariate polynomial** methods
- Being standardized by **NIST** for future internet use
- 🔐 Replaces RSA/ECC in long-term systems

### 2. 🔍 Zero-Knowledge Proofs (ZKPs)
- Allow a user to **prove something is true without revealing the actual data**
- Useful in **privacy-focused blockchain** (e.g., ZCash)
- Also used in authentication without password sharing

### 3. 🔒 Homomorphic Encryption
- Allows data to be processed while **still encrypted**
- Supports operations like addition and multiplication on ciphertexts
- Useful in **cloud computing**, healthcare, and finance
- Example: A cloud service can analyze encrypted medical data without ever seeing the actual data

---

## 💻 Python Demo – Simple Homomorphic Addition (Simulated)

```python
# Simulated homomorphic addition (concept only)
class SimpleHomomorphic:
    def __init__(self, key):
        self.key = key

    def encrypt(self, value):
        return value + self.key

    def decrypt(self, ciphertext):
        return ciphertext - self.key

    def add_encrypted(self, c1, c2):
        return c1 + c2

# Example
key = 5
crypto = SimpleHomomorphic(key)

e1 = crypto.encrypt(10)
e2 = crypto.encrypt(20)
e_sum = crypto.add_encrypted(e1, e2)
result = crypto.decrypt(e_sum)

print("Decrypted sum:", result)  # Output: 30
This is a toy example to explain the concept of homomorphic addition. Real systems like Paillier encryption support this securely.

🚀 Comparison Table
Technology	Quantum-Safe	Privacy-Preserving	Ready for Deployment?	Use Case
RSA / ECC	❌ No	❌ No	✅ Yes (for now)	Current web encryption
Lattice Crypto (PQC)	✅ Yes	❌ Not always	🚧 In development	Post-quantum web security
ZKPs	✅ Yes	✅ Yes	✅ Yes (in some projects)	Private blockchain, auth systems
Homomorphic Encrypt	✅ Yes	✅ Yes	🚧 Limited (still slow)	Secure cloud computation
💡 Reflection
This final week opened my eyes to how cryptography continues to evolve. I used to think that cryptographic systems like RSA and AES were "forever secure", but now I see that new threats like quantum computing are changing the game.

I was especially fascinated by zero-knowledge proofs — the idea that you can prove a fact without revealing the underlying secret feels like something out of science fiction, but it's real and working today.

Although technologies like homomorphic encryption are still slow, I can see how they will eventually let people analyze data without sacrificing privacy — which is a huge deal in fields like healthcare and finance.

🔗 Resources Consulted
NIST Post-Quantum Cryptography Project

YouTube – What is Homomorphic Encryption?

ZCash – How Zero-Knowledge Proofs Work
