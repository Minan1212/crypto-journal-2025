# Week 01 – Caesar Cipher

## 🔐 Topic Summary:
This week I learned about the **Caesar Cipher**, one of the earliest and simplest encryption techniques.

It works by shifting each letter of the plaintext by a fixed number of positions in the alphabet. For example, a shift of +3 means A becomes D, B becomes E, etc.

This cipher is **monoalphabetic** and **symmetric**, meaning the same key (shift value) is used for both encryption and decryption. It’s simple but not secure by today’s standards.

---

## ✍️ Manual Calculation

### Example:

- **Plaintext**: HELLO  
- **Shift**: +3  
- **Ciphertext**: KHOOR

**How it works:**

| Plaintext | H | E | L | L | O |
|-----------|---|---|---|---|---|
| Shift +3  | K | H | O | O | R |

So, “HELLO” becomes **KHOOR** when encrypted with a Caesar shift of 3.

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
This code encrypts any string by shifting each letter by the value of shift. It handles both uppercase and lowercase characters, and skips non-alphabetic ones.

⚔️ Possible Attacks
The Caesar Cipher is very weak and can be broken easily using:

Brute Force: Try all 25 possible shifts (only 26 letters in the alphabet)

Frequency Analysis: Analyze which letters appear most often to guess the plaintext (e.g., E, T, A in English)

It offers no real security in the modern world.

🔁 Comparison Table
Cipher	Type	Key Size	Security Level	Attack Resistance
Caesar Cipher	Monoalphabetic	1 number	Very Weak	Brute-force, frequency
💡 Reflection
I found Caesar Cipher very easy to understand and implement. It helped me grasp the basic idea of symmetric encryption and how alphabet shifting works in ciphers.

However, I also realized how outdated it is — since even someone with basic knowledge could break it in seconds using brute-force or frequency analysis.

It was a great introduction to classical encryption, but not suitable for securing real-world data.

🔗 Resources Consulted
Crypto101 – Caesar Cipher

YouTube – Caesar Cipher Explained

Wikipedia – Caesar Cipher
