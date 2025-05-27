# Cryptography
  Cryptography involves encrypting or decrypting a piece of data.

    Encryption/decryption tools and libraries such as openssl.
    Password cracking tools like John the Ripper and hashcat.
    Encoding/decoding and analysis tool like CyberChef.

### Understand the Types of Crypto Challenges

    Classical Ciphers:	Substitution, Caesar, Vigenère, etc.	ROT13, monoalphabetic
    Modern Crypto:	RSA, AES, ECC, DES, etc.	RSA low exponent, AES ECB mode
    Hashing / Encoding:	Hashes, Base64, etc.	MD5 collisions, decoding
    Custom / Broken Crypto:	Poorly designed schemes	XOR-based schemes, homebrew encryption
    Post-Quantum Crypto:	Lattice, code-based	NTRU, McEliece
    Quantum Simulations:	BB84 protocol	Simulated QKD data
    Stego/Crypto Hybrid:	Hidden data in files + crypto	Encrypted zip in image

### Crypto Challenge Solving Strategy

    Read the Challenge Description Carefully
        Look for hints: key size, algorithm type, block size, unusual formats.
        Identify any leaked keys, outputs, ciphertexts, plaintexts, etc.
    
    Identify the Algorithm or Technique
        Is it classical (Vigenère, Caesar)?
        Is it standard modern crypto (RSA, AES)?
        Is it custom encryption (XOR, shifting)?
    
    Try Known Attacks or Tools
        Known weakness? Use automated tools/scripts.
        Custom scheme? Analyze logic, look for flawed assumptions.
    
    Write or Use a Script to Exploit the Weakness
        Python is the go-to language (often with pwntools, pycryptodome, etc.).
        Break math problems using SageMath or SymPy.
    
    Test and Debug Carefully
        Ensure correct encoding (UTF-8 vs ASCII), padding (PKCS#7), etc.
    
    Get the Flag
        Usually looks like flag{something_here}

### Online Tools
- [dCode](https://www.dcode.fr): **crypto heaven**
- [Cryptii](https://cryptii.com): A web application that provides a suite of tools for encryption, decryption, and encoding.
- [Cryptii V2](https://cryptii.com): Version 2.
- [QuipQuip](https://quipqiup.com/): online **substitution cipher solver** with frequency analysis, also allows to insert frequency hints
- [Big Numbers Calculator 1](http://www.javascripter.net/math/calculators/100digitbigintcalculator.htm): an online **calculator for huge integers**
- [Big Numbers Calculator 2](https://defuse.ca/big-number-calculator.htm): an online **calculator for huge integers**, worse UI but maybe better performance
- [RSA Calculator](https://www.cryptool.org/en/cto/highlights/rsa-step-by-step): online **RSA parameters calculator with encryption/decryption**, works also with big numbers 
- [Inverse mod N Calculator](https://www.dcode.fr/modular-inverse): compute the **modular inverse of a number**, even with big numbers
- [FactorDB](http://factordb.com/): find **well-known integer factorization**
- [CrackStation](https://crackstation.net/): online **hash cracker** (md5, sha, ...)
- [Vigenere Solver](https://www.guballa.de/vigenere-solver): very good online **Vigenere Cipher solver** with bruteforce
- [Substitution Solver](https://www.guballa.de/substitution-solver): very good online **Substitution Cipher solver** with bruteforce
- [Sage Math](https://sagecell.sagemath.org/): online Sage environment to **perform Crypto calculations**
- [Crunch](https://tools.kali.org/password-attacks/crunch): Linux tool to **create custom dictionaries** for attacks (hash, pd, ..)
- [Online Hash Crack](https://www.onlinehashcrack.com/): big website to **perform hash/pwd cracking and identification** on various files
- [Hash Identifier](https://tools.kali.org/password-attacks/hash-identifier): Linux tool to **perform hash identification**
- [Morse Code Translator](https://morsecode.world/international/translator.html)
- [Dual Tone Decoder](http://dialabc.com/sound/detect/): find **DTMF tones** within audio clips
- [gmpy2](https://gmpy2.readthedocs.io/en/latest/intro.html): Python library for **multiple-precision arithmetic**

### Resources
- [Weird Ciphers](http://www.quadibloc.com/crypto/intro.htm): a list of some **strange cryptography algorithms**
- [Symbolic Ciphers](https://www.dcode.fr/symbols-ciphers): another list of **strange cryptography algorithms**

### Offline Tools
- FeatherDuster: A tool that can identify and exploit weaknesses in cryptographic implementations.
- Hash Extender: A tool for extending hash length attacks.
- padding-oracle-attacker: A tool for attacking padding oracle vulnerabilities in web applications.
- PkCrack: A tool for breaking PkZip encryption.
- [RsaCtfTool](https://github.com/Ganapati/RsaCtfTool): Python tool to perform **RSA attacks**
- RSATool: A tool for recovering the RSA private key from a given public key.
- XORTool: A tool for performing XOR encryption and decryption.
- Keyboard Shift: A tool for performing keyboard shift ciphers.


### Tips

    RSA-Based Attacks
        Low Exponent Attack (e = 3)
        Common Modulus Attack
        Hastad’s Broadcast Attack
        Wiener’s Attack (for small private key d)
    
    AES Pitfalls
        ECB Mode Detection
        Known IV leaks
        Padding Oracle Attacks
    
    XOR Crypto
        If known plaintext is present: ciphertext XOR plaintext = key
        Repeating key XOR can be brute-forced
    
    Hash Attacks
        Collision or Pre-image for weak hashes like MD5/SHA1
        Rainbow tables, dictionary attacks
