# Secure Key Management System (SKMS)

## Google Colab Notebook  
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1KSNEY1-4qhB8zJ1JVBdGf9a_khT7qNXk?usp=sharing)

## **Overview**
The Secure Key Management System (SKMS) is designed to manage cryptographic keys securely, ensuring **key generation, storage, exchange, and revocation**. This system supports both **symmetric (AES)** and **asymmetric encryption (RSA, Diffie-Hellman)** to protect communication and data integrity.

## **Features**
- **Key Generation**: Secure creation of AES and RSA keys.
- **Key Storage**: Encrypted storage of cryptographic keys.
- **Key Exchange**: Secure key distribution using Diffie-Hellman.
- **Key Revocation**: Detection and invalidation of compromised keys.
- **Security Mechanisms**:
  - Digital Signatures for authentication.
  - PKI-based certificate validation.
  - Key rotation and automatic revocation.

## **System Architecture**
The SKMS consists of the following components:
- **Centralized Key Distribution** for symmetric encryption.
- **Public Key Infrastructure (PKI)** for asymmetric encryption.
- **Key Verification** to ensure authenticity.
- **Secure Storage** using encrypted databases.

![System Flowchart](architecture.png)

## **Installation**
Ensure you have Python 3.8+ installed. Install the required dependencies using:

```bash
pip install -r requirements.txt
```

## Usage
### 1. Generating RSA Keys
```python
from cryptography.hazmat.primitives.asymmetric import rsa
from cryptography.hazmat.primitives import serialization

private_key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048
)from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
import os

key = os.urandom(32)  # 256-bit AES key
iv = os.urandom(16)   # Initialization Vector

cipher = Cipher(algorithms.AES(key), modes.CBC(iv))

public_key = private_key.public_key()
```

### 2. AES Encryption Example
```python
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
import os

key = os.urandom(32)  # 256-bit AES key
iv = os.urandom(16)   # Initialization Vector

cipher = Cipher(algorithms.AES(key), modes.CBC(iv))
```

## Security Considerations
### Mitigation Against Man-in-the-Middle (MITM) Attacks
-**Digital Signatures:** Used to authenticate RSA keys.
-**Certificate-Based Authentication:** Ensures trusted communication.
-**Authenticated Diffie-Hellman Key Exchange:** Prevents impersonation.

### Protection Against Key Compromise
-**Periodic Key Rotation:** Reduces the risk of key exposure.
-**Encrypted Key Storage:** Prevents unauthorized access.
-**Automated Key Revocation:** Ensures compromised keys are invalidated.

## Future Enhancements
-Quantum-Resistant Cryptography for long-term security.
-Blockchain-based Key Management for decentralized trust.
-AI-Powered Intrusion Detection to prevent unauthorized access.

License
This project is licensed under the MIT License.


