# Image Encryption & Decryption using RSA
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

A web-based application that demonstrates secure image encryption and decryption using the RSA (Rivest-Shamir-Adleman) asymmetric cryptographic algorithm. Built with Flask, this application provides an intuitive interface for users to encrypt images with customizable key sizes and decrypt them securely.





---

## Problem Statement

In the digital age, protecting sensitive visual data is crucial. Traditional symmetric encryption requires secure key exchange, which can be vulnerable to interception. Images often contain private or confidential information that needs robust protection during storage and transmission.

**Key challenges:**
- Secure transmission of images over untrusted networks
- Protection of sensitive visual data at rest
- Need for secure key management without pre-shared secrets
- Performance considerations when encrypting large binary files

---

## Solution Overview

This application implements RSA public-key cryptography to encrypt and decrypt images securely. By using asymmetric encryption:
- **Public keys** encrypt images, which can be freely distributed
- **Private keys** decrypt images, remaining confidential to the owner
- No need for pre-shared secrets between parties
- Provides configurable key sizes (512, 1024, 2048, 4096 bits) for varying security levels

The solution automatically handles chunked encryption to accommodate RSA's payload size limitations while processing large image files.

---

## Key Features

- **RSA Asymmetric Encryption**: Secure public-key cryptography implementation
- **Configurable Key Sizes**: Support for 512, 1024, 2048, and 4096-bit keys
- **Automatic Key Generation**: RSA key pairs generated on first launch
- **Chunked Processing**: Handles large images by splitting into encrypted chunks
- **Performance Metrics**: Real-time encryption/decryption time measurement
- **Web Interface**: Clean, responsive UI for easy operation
- **File Download**: Direct download of encrypted and decrypted files
- **Error Handling**: Comprehensive validation and error messages
- **Multiple Image Formats**: Support for JPEG, PNG, BMP, and other common formats

---





## Workflow

### Encryption Workflow
```
1. User uploads image + selects key size
2. Generate RSA key pair (public/private)
3. Read image as binary data
4. Split image into chunks (based on key size - 11 bytes for padding)
5. Encrypt each chunk using public key
6. Concatenate encrypted chunks
7. Save as .bin file
8. Measure and display encryption time
9. Provide download link
```

### Decryption Workflow
```
1. User uploads encrypted .bin file
2. Load private key from storage
3. Split encrypted data into chunks (based on key size)
4. Decrypt each chunk using private key
5. Concatenate decrypted chunks
6. Reconstruct original image
7. Measure and display decryption time
8. Provide download link
```

### Key Management
- Keys are auto-generated on first run if not present
- Stored as PEM files (`public_key.pem`, `private_key.pem`)
- Persistent across sessions
- Regenerated when user selects different key size

---

## Installation & Setup Instructions

### Prerequisites
- Python 3.7 or higher
- pip (Python package manager)

### Installation Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/SRIMATHI-RENGHARAJAN/image_encryption_rsa.git
   cd image_encryption_rsa
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   ```

3. **Activate virtual environment**
   - **Windows:**
     ```bash
     venv\Scripts\activate
     ```
   - **macOS/Linux:**
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies**
   ```bash
   pip install flask rsa
   ```

---

## How to Run the Project

1. **Navigate to project directory**
   ```bash
   cd image_encryption_rsa
   ```

2. **Run the Flask application**
   ```bash
   python app.py
   ```

3. **Access the application**
   - Open your web browser
   - Navigate to: `http://127.0.0.1:5000`

4. **Using the application**
   - **To Encrypt:** Upload an image, select key size, click "Encrypt and Download"
   - **To Decrypt:** Upload the `.bin` file, click "Upload Encrypted File and Get Image"

5. **Stop the server**
   - Press `Ctrl + C` in the terminal

---

## Project Structure

```
image_encryption_rsa/
│
├── app.py                    # Main Flask application
├── templates/
│   └── index.html           # Web interface template
├── uploads/                 # Directory for uploaded/encrypted files
│   └── effect_encrypted.txt # Sample encrypted file
├── public_key.pem           # Auto-generated RSA public key
├── private_key.pem          # Auto-generated RSA private key
├── venv/                    # Virtual environment (not in repo)
└── README.md                # Project documentation
```

---

## Results 

### Performance Metrics
The application measures and displays:
- **Encryption Time**: Time taken to encrypt the image (in seconds)
- **Decryption Time**: Time taken to decrypt the image (in seconds)

### Key Size Impact
| Key Size (bits) | Security Level | Speed | Max Chunk Size |
|----------------|----------------|-------|----------------|
| 512            | Low            | Fast  | 53 bytes       |
| 1024           | Medium         | Moderate | 117 bytes   |
| 2048           | High           | Slower | 245 bytes     |
| 4096           | Very High      | Slowest | 501 bytes    |

### Output Files
- **Encrypted File**: `[original_name]_encrypted.bin` - Binary encrypted data
- **Decrypted File**: `decrypted_image.jpg` - Restored original image

---


## License

Use for educational and commercial purposes with proper attribution.



---

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## Author

**SRIMATHI RENGHARAJAN**
- GitHub: https://github.com/SRIMATHI-RENGHARAJAN
- Linkedin: https://www.linkedin.com/in/srimathi-rengharajan/


---

## Acknowledgments

- RSA algorithm by Rivest, Shamir, and Adleman
- Python RSA library by Sybren A. Stüvel
- Flask framework by Armin Ronacher
- Inspiration from cryptography and information security best practices

---

