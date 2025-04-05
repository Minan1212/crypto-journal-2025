
# Week 01 – Caesar Cipher

## 🔐 Topic Summary:
This week I learned about the **Caesar Cipher**, one of the earliest and most basic encryption techniques.

The Caesar Cipher works by **shifting each letter in the plaintext by a fixed number of positions** in the alphabet. For example, a shift of +3 transforms A into D, B into E, and so on.

It is a **monoalphabetic substitution cipher** and **symmetric**, meaning the same key is used for both encryption and decryption.

While it's easy to implement and understand, it offers **very weak security** and is not used in real-world systems.

---

## ✍️ Manual Calculation

### Example:

- **Plaintext**: HELLO  
- **Shift**: +3  
- **Ciphertext**: KHOOR

**Step-by-step shift:**

| Plaintext | H | E | L | L | O |
|-----------|---|---|---|---|---|
| +3 Shift  | K | H | O | O | R |

So, using Caesar Cipher with a shift of 3, the word **HELLO** becomes **KHOOR**.

---

## 💻 Python Code – Caesar Cipher

```python
def caesar_encrypt(text, shift):
    result = ''
    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char
    return result

print(caesar_encrypt("HELLO", 3))  # Output: KHOOR
⚔️ Possible Attacks
The Caesar Cipher is not secure and can be easily broken using:

Brute Force Attack: Try all 25 possible shifts (since there are only 26 letters).

Frequency Analysis: Common letters in English (like E, T, A) make it easy to guess the plaintext.

For this reason, Caesar Cipher is considered insecure today and is mainly used for educational purposes.

🔁 Comparison Table
Cipher	Type	Key Size	Security Level	Attack Resistance
Caesar Cipher	Monoalphabetic	1 number	Very Weak	Brute-force, frequency
💡 Reflection
This week helped me understand the basic principles of symmetric encryption. I enjoyed manually solving and writing the Caesar cipher in Python.

At first, it seemed like a clever way to hide messages, but I quickly realized how vulnerable it is. The fact that it can be broken in seconds using brute-force or frequency analysis shows how important stronger encryption is in modern systems.

This was a great introduction to cryptography and helped me appreciate why key management and randomness are important for security.

🔗 Resources Consulted
Crypto101 – Caesar Cipher

YouTube – Caesar Cipher Explained

Wikipedia – Caesar Cipher
