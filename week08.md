# Week 08 – Public Key Infrastructure (PKI) & Certificates

## 🔐 Topic Summary:
This week I explored **Public Key Infrastructure (PKI)**, which is the system that enables **secure communication, trust, and identity verification** on the internet.

PKI is based on **asymmetric cryptography**, where:
- Each user has a **public and private key**
- The public key is shared in a **digital certificate**
- The certificate is issued and verified by a trusted **Certificate Authority (CA)**

PKI ensures:
- 🔒 Confidentiality (via encryption)
- ✅ Authentication (via certificates)
- 🛡 Integrity (via digital signatures)

PKI is the backbone of secure web browsing (HTTPS), digital signatures, software updates, and VPN authentication.

---

## 🧠 Manual Understanding – How Certificates Work

### Example Process:

1. Website (e.g., `example.com`) creates a public/private key pair  
2. Sends a **Certificate Signing Request (CSR)** to a trusted **CA**  
3. CA verifies the identity of the site and issues a **Digital Certificate** containing:
   - Website’s public key
   - Domain name
   - CA’s digital signature

4. When a user visits the site:
   - Browser checks the certificate
   - Verifies it’s signed by a trusted CA
   - Uses the **public key** to securely exchange a session key (via TLS handshake)

---

## 💻 Python Demo – Generate RSA Key Pair & Self-Signed Certificate (using OpenSSL)

> 🔧 Use the terminal with OpenSSL installed:

```bash
# Generate private key
openssl genrsa -out private.key 2048

# Generate CSR
openssl req -new -key private.key -out request.csr

# Generate self-signed certificate (valid for 365 days)
openssl x509 -req -in request.csr -signkey private.key -out certificate.crt -days 365
This process simulates how a website or service can create its own certificate.
Browsers trust certificates signed by recognized CAs, not self-signed ones.

⚠️ PKI Risks and Attacks
Certificate Spoofing: Attackers use fake certs to impersonate websites.

Compromised CAs: If a CA is hacked, all certificates it issued are no longer trusted.

Expired Certificates: Can break services if not renewed in time.

Mitigation:
Use certificate pinning

Monitor and renew certificates on time

Use Certificate Transparency Logs

🔁 Comparison Table – Certificates
Feature	Self-Signed Cert	CA-Issued Certificate
Trusted by Browsers	❌ No	✅ Yes
Use Case	Internal, testing only	Public websites, production
Cost	Free	May cost money (Let’s Encrypt is free)
Verified Identity	❌ No	✅ Yes
💡 Reflection
Before this week, I thought HTTPS was just “secure.” Now I understand that it’s PKI and certificates that make it possible to verify the website and protect data.

I also learned about the importance of trust chains — your browser doesn’t trust websites directly, it trusts the CAs that signed their certificates. If the CA is compromised, trust is broken.

Using OpenSSL showed me how to actually generate a certificate and understand what’s inside it. I now know why browsers show certificate warnings — and why expired or untrusted certs should never be ignored.

🔗 Resources Consulted
Crypto101 – Public Key Infrastructure

OpenSSL Commands Reference

YouTube – How HTTPS Works

yaml
Copy code
