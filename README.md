# Securing_Netcat

## Netcat

“Netcat (often abbreviated to nc) is a computer networking utility for reading from and writing to network connections using TCP or UDP. The command is designed to be a dependable back-end that can be used directly or easily driven by other programs and scripts. At the same time, it is a feature-rich network debugging and investigation tool, since it can produce almost any kind of connection its user could need and has a number of built-in capabilities. Its list of features includes port scanning, transferring files, and port listening: as with any server, it can be used as a backdoor.”

## Enhancement

To avoid some of the risks identified in your security analysis, this project provide some enhancements to increase the security of netcat. Design, implement and document enhancements to increase the security of netcat. 
It enforce security principles of
    i. Data confidentiality 
    ii. Data integrity
    iii. Device authentication

## Approach

This project has enhanced the security of the basic Netcat-based code. 

After establishing a connection, both parties use the DH algorithm to negotiate a shared secret key through a public channel. During message or file transmission, both parties use AES-CCM mode for encryption. In the encryption process, the strength of the key is enhanced by using the previously negotiated shared secret key, randomly generated nonce value, salt value, and MAC length (mac_len).

DH algorithm allows the two communicating parties to negotiate a shared secret key over a public channel. The DH algorithm works by generating a pair of public and private keys for each party, where the public key can be shared while the private key remains secret. The parties exchange their public keys over the public channel and use their private key and the other party’s public key to compute a shared secret key. As only the parties know their own private keys, this ensures the security of the shared secret key.

After obtaining the shared secret key, both parties use the PBKDF2 (Password-Based Key Derivation Function 2) function and AES-CCM mode for encrypting and decrypting the data. PBKDF2 is a key derivation function used to derive the encryption key from the password. It requires entering the password, salt value, and number of iterations, and generating a derived key of the required length . Salt values are used to add randomness, and the number of iterations determines the number of applications of the function, making the key derivation process slower and safer.

Cipher block chaining - message authentication code (AES-CCM) mode combines the counter mode encryption with CBC-MAC authentication. It can provide both encryption and authen- tication security guarantees simultaneously. In AES-CCM mode, the MAC and the encryption process are carried out at the same time, that is to say, the MAC is calculated during the encryption process to ensure the integrity and authentication of the encrypted data.