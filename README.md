RSA Encryption & Digital Signature CLI
This project is a command-line interface (CLI) tool written in Python to demonstrate the principles of the RSA (Rivest–Shamir–Adleman) cryptographic algorithm. It allows users to generate RSA keys, encrypt and decrypt messages, and create and verify digital signatures in an interactive and easy-to-understand way.
The primary goal of this tool is educational. It visualizes the steps involved in RSA, making it an excellent resource for learning about asymmetric cryptography.
Disclaimer: For Educational Use Only
This implementation is designed for learning purposes and should not be used for real-world security applications. It has several simplifications that make it insecure for production use:
Small Key Sizes: The prime numbers generated are too small to provide meaningful security.
Basic Primality Test: The is_prime function uses a simple trial division method, which is inefficient for the large primes required for secure RSA.
No Padding Scheme: Secure RSA implementations use padding schemes (like OAEP or PKCS#1 v1.5) to prevent common cryptographic attacks. This script encrypts raw character data, which is vulnerable.
Simplified Hashing: The digital signature feature uses a very simple and insecure hash function (sum of ASCII values). Real-world applications use cryptographically secure hash algorithms like SHA-256.
Features
🔑 RSA Key Generation: Generate public and private key pairs with varying (demonstrative) key sizes.
🔒 Message Encryption: Encrypt text messages using a generated public key.
🔓 Message Decryption: Decrypt ciphertext back to the original message using the corresponding private key.
✍️ Digital Signatures: Create a digital signature for a message to ensure its authenticity and integrity.
🔍 Signature Verification: Verify a digital signature using the public key.
🧮 Mathematical Walkthrough: A special mode that demonstrates the core RSA mathematics with small, easy-to-follow prime numbers.
⚙️ Interactive & Verbose CLI: An easy-to-use menu-driven interface with detailed printouts explaining each step of the process.
Prerequisites
Python 3.x
No external libraries are needed, as this script only uses the random, math, and sys modules.

Usage Walkthrough
Here is a typical session with the tool:
Generate Keys: Start by selecting option 1. The program will generate two distinct prime numbers, p and q, and then calculate n, phi(n), e, and d. The public and private keys will be displayed.
Encrypt a Message: Select option 2 and enter a message (e.g., "hello"). The tool will show the character-by-character encryption process, converting each character to its ASCII value and then applying the formula c = m^e mod n. The resulting list of numbers is your ciphertext.
Decrypt a Message: Select option 3. The tool will use the stored ciphertext and the private key to decrypt the message. It will show the character-by-character decryption process, applying the formula m = c^d mod n, and then convert the resulting ASCII values back to characters to reveal the original message.
Sign a Message: Select option 4 and enter a message. The program calculates a simple hash of the message and "encrypts" this hash with the private key to create a signature.
Verify a Signature: Select option 5. The program takes the original message and the signature, "decrypts" the signature with the public key to retrieve the original hash, and compares it with a newly computed hash of the message to check for validity.
Code Breakdown
The script is structured into a main class and several functions to handle the user interface.
RSAEncryption Class
This class encapsulates all the logic related to the RSA algorithm.
Method	Description
is_prime(num)	A basic function to check if a number is prime.
generate_prime(...)	Generates a random prime number within a specified range.
gcd(a, b)	Calculates the Greatest Common Divisor using the Euclidean algorithm.
mod_inverse(e, phi)	Calculates the modular multiplicative inverse d using the Extended Euclidean Algorithm.
generate_keys(...)	The core function that orchestrates the generation of p, q, n, phi, e, and d.
encrypt_message(...)	Takes a string and encrypts it character-by-character using the public key.
decrypt_message(...)	Takes a list of encrypted integers and decrypts them using the private key.
sign_message(...)	Creates a digital signature for a message using a simple hash and the private key.
verify_signature(...)	Verifies a signature's authenticity using the public key.
UI and Helper Functions
Function	Description
display_menu()	Prints the main menu of options to the console.
mathematics_demo()	A self-contained function to demonstrate the RSA math with small, fixed numbers for clarity.
main()	The main application loop that handles user input, calls the appropriate methods from the RSAEncryption class, and manages the program's state.
