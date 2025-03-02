# AES-256-CBC File Encryption and Decryption in Rust

This Rust application provides a secure way to encrypt and decrypt files using the AES-256-CBC encryption algorithm. It leverages PBKDF2 for key derivation from a passphrase and employs a zero-initialized initialization vector (IV) for both encryption and decryption operations.

This project was inspired by and builds upon concepts from the video *["Getting Started with Rust - Bypass Windows Defender"](https://www.youtube.com/watch?v=o8af1KeMrRc&list=PLRlFYFaJSu7J5e0Jxz2kyzOWeRi4NJyHD&index=85)* by **[Gemini Cyber Security](https://www.youtube.com/@gemini_security)**. However, if Windows Defender flagged their tool's signature, the code was modified to ensure it does not share the same signature while maintaining its core functionality. **[Gemini Cyber Security](https://www.youtube.com/@gemini_security)**. Credit goes to them for providing an excellent introduction to Rust programming that helped shape this tool.

## Features
- **AES-256-CBC Encryption**: Implements the industry-standard AES-256 algorithm in Cipher Block Chaining (CBC) mode.
- **PBKDF2 Key Derivation**: Derives a secure encryption key from a user-provided passphrase.
- **File Encryption and Decryption**: Supports encrypting and decrypting files of arbitrary size.
- **Key Storage**: Automatically stores the derived encryption key in a `key.txt` file for later use.

## Prerequisites
To use this application, ensure that Rust is installed on your system. If you don’t have Rust installed, you can install it via Rustup with the following command:

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Follow the on-screen instructions to complete the installation.

## Building the Project

### 1. Clone the Repository
Clone this repository and navigate to the project directory:

```sh
git clone <repository_url>
cd <repository_name>
```

### 2. Install Dependencies
The project relies on several Rust crates. Ensure your `Cargo.toml` includes the following dependencies:

```toml
[dependencies]
aes = "0.8"
block-modes = "0.8"
pbkdf2 = "0.12"
sha2 = "0.10"
hex = "0.4"
hmac = "0.12"
```

Then, build the project in release mode:

```sh
cargo build --release
```

The compiled binary will be located in the `target/release` directory.

## Usage
Run the application using the compiled binary (`rust`) with the following commands:

### Encrypt a File
To encrypt a file:

```sh
./target/release/rust -encrypt <input_filename>
```

Example:

```sh
./target/release/rust -encrypt example.txt
```

This generates:
- An encrypted file named `<input_filename>_encrypted` (e.g., `example.txt_encrypted`).
- A `key.txt` file containing the derived encryption key.

### Decrypt a File
To decrypt a file:

```sh
./target/release/rust -decrypt <input_filename> <key_filename>
```

Example:

```sh
./target/release/rust -decrypt example.txt_encrypted key.txt
```

This generates a decrypted file named `decrypted.bin`.

## Security Considerations
- **Initialization Vector (IV)**: The IV is currently set to zero, which is not recommended for production use due to security risks. For enhanced security, consider modifying the code to use a cryptographically secure random IV.
- **Key Storage**: The encryption key is stored in plain text in `key.txt`. Ensure this file is stored securely and excluded from version control (e.g., via `.gitignore`).
- **Passphrase**: The application currently uses a hardcoded passphrase. For real-world applications, replace this with a secure user input mechanism.

## Credits
Special thanks to **Gemini Cyber Security** for their insightful video *"Getting Started with Rust - Bypass Windows Defender"*, which provided foundational knowledge and inspiration for this project.

## License
This project is licensed under the **MIT License**. See the `LICENSE` file for details.

