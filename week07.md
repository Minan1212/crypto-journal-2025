# Week 07 – Key Exchange Protocols (Diffie-Hellman)

## 🔐 Topic Summary:
This week I learned about **key exchange protocols**, especially the **Diffie-Hellman Key Exchange (DHKE)**.

Key exchange protocols are used to **securely share a secret key** between two parties over an insecure channel. The most famous is the **Diffie-Hellman algorithm**, which was the first practical solution to this problem.

Diffie-Hellman enables both parties to compute the same secret without ever transmitting it, using modular arithmetic and exponentiation.

It is commonly used in:
- HTTPS (TLS)
- VPNs
- Secure messaging apps (e.g., Signal, WhatsApp)

---

## 🔄 Manual Understanding – Diffie-Hellman Example

### Example Steps:
1. Alice and Bob publicly agree on:
   - Prime `p = 23`
   - Generator `g = 5`

2. Alice picks secret `a = 6`  
   - Computes `A = g^a mod p = 5^6 mod 23 = 8`

3. Bob picks secret `b = 15`  
   - Computes `B = g^b mod p = 5^15 mod 23 = 2`

4. Exchange:
   - Alice sends A = 8 to Bob  
   - Bob sends B = 2 to Alice

5. Compute shared secret:
   - Alice: `s = B^a mod p = 2^6 mod 23 = 18`
   - Bob: `s = A^b mod p = 8^15 mod 23 = 18`

✅ Both get the same secret: `18`, even though they never sent it directly.

---

## 💻 Python Code – Diffie-Hellman Key Exchange

```python
# Simple DHKE example (not secure for real use)

# Public values
p = 23  # prime
g = 5   # generator

# Private keys
a = 6   # Alice's secret
b = 15  # Bob's secret

# Public keys
A = pow(g, a, p)  # Alice sends this
B = pow(g, b, p)  # Bob sends this

# Shared secrets
alice_shared = pow(B, a, p)
bob_shared = pow(A, b, p)

print("Alice's Shared Secret:", alice_shared)
print("Bob's Shared Secret:", bob_shared)
This simulation shows how Alice and Bob can compute the same shared secret independently.

⚠️ Security Considerations
No authentication: DH alone doesn't verify who you're talking to. This opens the door for Man-in-the-Middle (MITM) attacks.

Needs large primes: Real systems use 2048-bit primes or more.

Perfect Forward Secrecy (PFS): DH is often used with ephemeral keys (DHE) to support PFS.

🔁 Comparison Table – Key Exchange Methods
Method	Type	Authentication	Secure?	Notes
Diffie-Hellman	Asymmetric	❌ No	✅ Yes (with big p)	Used in TLS, needs PFS support
RSA Key Exchange	Asymmetric	✅ Yes	✅ Yes	Slower, but widely supported
Pre-Shared Key	Symmetric	✅ Yes	❌ Risky	Easy, but not scalable
💡 Reflection
I found this week really interesting. I used to think that two people had to send a password to share a key. But now I see how math allows two people to agree on a key without sharing it directly.

The Python code helped me understand the math behind it — and I was surprised how elegant the process is. It also helped me appreciate the importance of authentication, because DH alone doesn’t verify who’s on the other end.

This week also introduced the idea of Perfect Forward Secrecy, which I had heard about but didn’t fully understand before.

🔗 Resources Consulted
Crypto101 – Diffie-Hellman Key Exchange

YouTube – Diffie-Hellman Explained Visually

Python pow() for modular exponentiation
