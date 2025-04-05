# Week 05 – Hash Functions

## 🔐 Topic Summary:
This week I learned about **cryptographic hash functions**, which are algorithms that take an input (message) and produce a fixed-size string of characters, known as a **hash** or **digest**.

A good hash function must have the following properties:

- **Deterministic**: Same input → same output
- **Fast computation**
- **Pre-image resistance**: Hard to reverse
- **Second pre-image resistance**: Hard to find a different input with the same output
- **Collision resistance**: Hard to find two different inputs with the same hash

Popular hash functions include **MD5**, **SHA-1**, and **SHA-2 (like SHA-256)**. MD5 and SHA-1 are now considered broken.

---

## 🧠 Manual Understanding – Hashing Examples

### Example:

Hashing the same string using different algorithms:

- Input: `"Hello"`
- MD5 → `8b1a9953c4611296a827abf8c47804d7`
- SHA1 → `f7ff9e8b7bb2b91af11c3e10d3c88daf95f3c1c1`
- SHA256 → `185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969`

Changing just **one letter** completely changes the output — this is known as the **avalanche effect**.

---

## 💻 Python Code – Hash Functions with `hashlib`

```python
import hashlib

text = "Hello"

# MD5
md5_hash = hashlib.md5(text.encode()).hexdigest()
print("MD5:", md5_hash)

# SHA1
sha1_hash = hashlib.sha1(text.encode()).hexdigest()
print("SHA1:", sha1_hash)

# SHA256
sha256_hash = hashlib.sha256(text.encode()).hexdigest()
print("SHA256:", sha256_hash)
