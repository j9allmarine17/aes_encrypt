AES-256-CBC File Encryption and Decryption in Rust

This Rust program encrypts and decrypts files using the AES-256-CBC encryption scheme. It derives an encryption key from a passphrase using PBKDF2 and uses a zero-initialized IV for encryption and decryption.

Features

AES-256-CBC encryption

PBKDF2 key derivation

File encryption and decryption

Automatic key storage in key.txt

Prerequisites

Ensure you have Rust installed on your system. If Rust is not installed, you can install it using Rustup:

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

Building the Project

Clone this repository and navigate into the project directory:

git clone <repository_url>
cd <repository_name>

Install Dependencies

Ensure you have the required Rust dependencies by adding them to Cargo.toml:

[dependencies]
aes = "0.8"
block-modes = "0.8"
pbkdf2 = "0.12"
sha2 = "0.10"
hex = "0.4"
hmac = "0.12"

Then, build the project:

cargo build --release

Usage

Run the compiled binary with the following commands:

Encrypt a File

./rust -encrypt <input_filename>

Example:

./rust -encrypt example.txt

This will generate an encrypted file named example.txt_encrypted and a key.txt file containing the encryption key.

Decrypt a File

./rust -decrypt <input_filename> <key_filename>

Example:

./rust -decrypt example.txt_encrypted key.txt

This will generate a decrypted file named decrypted.bin.

Security Considerations

The IV is initialized to zero, which is not recommended for security-sensitive applications. Consider using a random IV for improved security.

The key is stored in key.txt, which should be handled securely.

The passphrase should be replaced with a secure user input mechanism instead of a hardcoded value.

License

This project is licensed under the MIT License. See the LICENSE file for more details.

