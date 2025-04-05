# Week 04 – AES and Block Cipher Modes

## 🔐 Topic Summary:
This week I learned about **Advanced Encryption Standard (AES)**, a modern symmetric key encryption algorithm used worldwide to secure sensitive data.

AES operates on blocks of data and supports key sizes of **128, 192, or 256 bits**. It uses multiple rounds of substitution, permutation, and mixing.

I also learned about **block cipher modes of operation**, which define how blocks are chained during encryption. These include:

- **ECB (Electronic Code Book)** – encrypts each block independently  
- **CBC (Cipher Block Chaining)** – each block depends on the previous one  
- **CFB/OFB/CTR** – stream-like encryption with feedback or counters

---

## 🔄 Manual Understanding – ECB vs. CBC

### ECB Mode:
- Each block is encrypted separately.
- Identical plaintext blocks result in identical ciphertext blocks.
- **Not secure for patterns** (e.g., image encryption shows shapes).

### CBC Mode:
- Each plaintext block is XORed with the previous ciphertext block before encryption.
- Requires an **IV (Initialization Vector)** for the first block.
- Much more secure than ECB.

---

## 💻 Python Code – AES Encryption (ECB & CBC using `pycryptodome`)

> 🔧 Note: You must install `pycryptodome`  
> `pip install pycryptodome`

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

# Setup
key = get_random_bytes(16)  # 128-bit key
data = b"Secret Message!!"  # 16-byte block

# ECB Mode
cipher_ecb = AES.new(key, AES.MODE_ECB)
ciphertext_ecb = cipher_ecb.encrypt(pad(data, 16))
print("ECB Encrypted:", ciphertext_ecb)

# CBC Mode
iv = get_random_bytes(16)
cipher_cbc = AES.new(key, AES.MODE_CBC, iv)
ciphertext_cbc = cipher_cbc.encrypt(pad(data, 16))
print("CBC Encrypted:", ciphertext_cbc)
This code demonstrates AES in ECB and CBC mode. CBC adds randomness with an IV, making the output more secure.

⚔️ Possible Attacks and Considerations
ECB Mode Weakness: Patterns in plaintext appear in ciphertext.

CBC Mode is better, but:

Needs secure IV generation and storage.

Slower due to chaining process.

🔁 Comparison Table – AES Modes
Mode	Description	Pattern Leaks	IV Needed	Use Case
ECB	Encrypts blocks independently	✅ Yes	❌ No	NEVER use for real data
CBC	XOR with previous ciphertext	❌ No	✅ Yes	Secure files, messages
CTR	Uses counter-based stream	❌ No	✅ Yes	Network encryption
💡 Reflection
This week gave me a deep appreciation for how modern encryption systems protect data. I used to think AES alone was secure, but I now understand that mode of operation is just as important.

I was surprised how insecure ECB mode is, even with a strong cipher like AES. The CBC mode, while better, still relies on correct use of IVs and padding.

Implementing both modes in Python helped me understand how these systems work under the hood. I now understand why modern applications avoid ECB and often prefer CBC or CTR.

🔗 Resources Consulted
Crypto101 – Block Cipher Modes

PyCryptodome Docs – AES Modes

YouTube – ECB vs CBC Explained
