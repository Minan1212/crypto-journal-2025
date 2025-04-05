# Week 02 – Substitution and Vigenère Ciphers

## 🔐 Topic Summary:
This week focused on classical ciphers, specifically:

- **Monoalphabetic Substitution Cipher**: A cipher where each letter in the plaintext is replaced with another letter using a fixed substitution pattern.
- **Vigenère Cipher**: A polyalphabetic cipher that uses a repeating keyword to vary the Caesar shift across the plaintext.

These ciphers help illustrate the evolution from simple encryption to stronger, key-based systems.

---

## ✍️ Manual Working – Vigenère Cipher Example

### Example:

- **Plaintext**: ATTACKATDAWN  
- **Keyword**: LEMON  
- **Key repeated to match length**: LEMONLEMONLE  
- **Ciphertext**: LXFOPVEFRNHR

| Plaintext | A | T | T | A | C | K | A | T | D | A | W | N |
|-----------|---|---|---|---|---|---|---|---|---|---|---|---|
| Key       | L | E | M | O | N | L | E | M | O | N | L | E |
| Cipher    | L | X | F | O | P | V | E | F | R | N | H | R |

This manual calculation helped reinforce how the shifts change depending on the keyword.

---

## 💻 Python Code – Vigenère Cipher

```python
def vigenere_encrypt(plaintext, key):
    encrypted = []
    key = key.upper()
    for i, char in enumerate(plaintext.upper()):
        if char.isalpha():
            shift = ord(key[i % len(key)]) - ord('A')
            encrypted_char = chr((ord(char) - ord('A') + shift) % 26 + ord('A'))
            encrypted.append(encrypted_char)
        else:
            encrypted.append(char)
    return ''.join(encrypted)

print(vigenere_encrypt("ATTACKATDAWN", "LEMON"))  # Output: LXFOPVEFRNHR
I tested this code to confirm my manual calculation was correct. It showed how the keyword influences the encryption dynamically.

⚔️ Attacks on These Ciphers:
Substitution Cipher:
Frequency Analysis: Since each letter maps to the same one, it’s easy to spot common letters like E or T in English.

Very weak by today’s standards.

Vigenère Cipher:
Harder to attack due to changing letter mappings.

Still vulnerable to:

Kasiski Examination: Helps determine key length by finding repeated patterns.

Friedman Test: Uses statistics to estimate key length.

🔁 Comparison Table:
Cipher Type	Key Type	Strength	Attack Resistance
Caesar Cipher	Fixed Shift	Very Weak	Easily brute-forced
Substitution Cipher	1:1 Mapping	Weak	Broken by frequency analysis
Vigenère Cipher	Repeating Keyword	Moderate	Resists simple frequency
💡 Reflection:
At first, I believed the Vigenère cipher was unbreakable, but after learning about Kasiski and Friedman attacks, I understood that security depends on key length and randomness.
I found the Python implementation really helpful for visualizing how the encryption works step by step.

This week helped me realize how ciphers evolved to become more resistant to attacks, and how adding variation (like a keyword) strengthens encryption significantly.

🔗 Resources Consulted:
Crypto101 – Introduction to Classical Ciphers

Computerphile – Vigenère Cipher Explained

Wikipedia – Vigenère Cipher
