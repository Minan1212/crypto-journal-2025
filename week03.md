# Week 03 – One-Time Pad & XOR Cipher

## 🔐 Topic Summary:
This week I learned about **One-Time Pad (OTP)** and the concept of **XOR encryption**.

The One-Time Pad is a cipher where:
- The key is truly random
- The key is as long as the message
- The key is used **only once**

When used correctly, the One-Time Pad offers **perfect secrecy**, meaning it is mathematically unbreakable.

Both OTP and simple XOR-based ciphers use the **XOR (exclusive OR)** operation to encrypt and decrypt messages.

---

## ✍️ Manual XOR Working

### Example:

- **Plaintext** character: H → `01001000`  
- **Key** character:       X → `01011000`  
- **XOR Result**:          `00010000` → `` (non-printable character)

XOR flips bits only where the bits differ. It's symmetric, so:

Ciphertext = Plaintext XOR Key
Plaintext = Ciphertext XOR Key

python
Copy code

---

## 💻 Python Code – XOR Cipher

```python
def xor_encrypt_decrypt(text, key):
    result = ''
    for i in range(len(text)):
        result += chr(ord(text[i]) ^ ord(key[i % len(key)]))
    return result

# Encrypt
plaintext = "HELLO"
key = "XMCKL"
cipher = xor_encrypt_decrypt(plaintext, key)
print("Ciphertext:", cipher)

# Decrypt (same function)
decrypted = xor_encrypt_decrypt(cipher, key)
print("Decrypted:", decrypted)
This code demonstrates how XOR encryption works. You can use the same function to decrypt the message by passing in the ciphertext and the key.

⚔️ Possible Attacks
✅ One-Time Pad:
Unbreakable if:

The key is truly random

The key is never reused

The key is kept secret

❌ BUT — Real-World Problems:
Generating truly random keys is difficult

Key must be as long as the message

Secure key sharing is challenging

If the key is reused → Vulnerable to ciphertext comparison attacks (e.g., Crib-dragging)

🔁 Comparison Table
Cipher	Key Length	Security	Reusability	Notes
Caesar	1 character	Very Weak	Yes	Easy to brute-force
Vigenère	Short keyword	Moderate	Yes	Weak if key is short
One-Time Pad	Same as message	Perfect (theoretical)	No	Requires perfect key handling
XOR Cipher	Varies	Weak (on its own)	Yes	Only secure with OTP-style key
💡 Reflection:
This week really showed me how XOR works at the binary level, and how something so simple can be used for both strong and weak encryption — depending on how the key is handled.

I was impressed by the One-Time Pad because it offers unbreakable security, but I also realized why it’s not practical: key distribution is too difficult in real-world scenarios.

The Python XOR demo helped me understand how the same function can be used for both encryption and decryption, which made the logic of symmetric encryption really clear.

🔗 Resources Consulted:
YouTube – One-Time Pad Explained

Crypto101 – XOR and OTP

Wikipedia – One-Time Pad
