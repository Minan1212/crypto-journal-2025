# Week 01 – Caesar Cipher

## 🔐 Topic Summary:
Learned about Caesar Cipher, which shifts each letter by a fixed value. It was one of the earliest known ciphers and represents basic principles of symmetric encryption.

## ✍️ Manual Calculation:
Plaintext: HELLO  
Shift: +3  
Ciphertext: KHOOR

## 💻 Python Code:

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

print(caesar_encrypt("HELLO", 3))
 Possible Attacks:
Brute-force: Try all 25 shifts

Frequency analysis: Match common letters

🔁 Comparison:
Cipher	Type	Strength
Caesar	Monoalphabetic	Weak
💡 Reflection:
I learned Caesar is very weak today and can be broken easily using simple methods.

🔗 Resources:
https://crypto101.io

https://www.youtube.com/watch?v=sMOZf4GN3oc
