# Browser Password Decrypt

Browser Password Decrypt is a tool to decrypt passwords stored by popular browsers. It can decrypt passwords from Chrome, Opera, Edge and Brave.

For FireFox: [click here](https://github.com/unode/firefox_decrypt)

## Features

- Extracts saved passwords from Chrome, Opera, Edge and Brave browser.
- Allows selection of specific user profiles.
- Decrypts the passwords using the secret key from the Local State file.
- Saves the decrypted passwords to a CSV file.

## Installation

```bash
# Cloning the Repository
gh repo clone SOME-1HING/browser_password_decrypt

cd browser_password_decrypt

# Install Dependencies
pip install -r requirements.txt
```

## Usage

```bash
# Run the script
py main.py
```

## How it Works

In today's digitally interconnected world, the convenience of web browsers saving passwords can't be overstated. Yet, this seemingly innocuous feature also raises pertinent questions about the security of our digital identities. In this comprehensive exploration, we'll unravel the complexities of browser password encryption, with a primary focus on AES (Advanced Encryption Standard), delve into the mechanics of Python scripts for password decryption, scrutinize the associated security risks, and propose strategies for fortifying cybersecurity measures.

### Understanding AES Encryption

At the heart of browser password encryption lies AES, a robust symmetric key algorithm widely lauded for its security and efficiency. AES operates on a single secret key for both encryption and decryption, ensuring seamless data protection. Additionally, AES encryption often integrates an initialization vector (IV) to inject randomness, bolstering the cryptographic resilience against malicious attacks.

```python
from Cryptodome.Cipher import AES

# Assume you have obtained the secret key and initialization vector from the Chrome files
secret_key = b'Sixteen byte key'  # Replace with your actual secret key
initialization_vector = b'RandomIVString12'  # Replace with your actual initialization vector

# Assume you have obtained the encrypted password from the Chrome files
ciphertext = b'YourEncryptedPasswordHere'  # Replace with your actual encrypted password

# Step 1: Extract initialization vector from ciphertext
initialization_vector = ciphertext[3:15]

# Step 2: Extract encrypted password from ciphertext
encrypted_password = ciphertext[15:-16]

# Step 3: Build the AES algorithm to decrypt the password
cipher = AES.new(secret_key, AES.MODE_GCM, initialization_vector)
decrypted_pass = cipher.decrypt(encrypted_password)

# Step 4: Decrypted Password
print(decrypted_pass.decode())

```

#### Where does different browsers store the encryption key?

- Google Chrome: `C:\Users\<PC Name>\AppData\Local\Google\Chrome\User Data\Local State`
- Microsoft Edge: `C:\Users\<PC Name>\AppData\Local\Microsoft\Edge\User Data\Local State`
- Firefox: `C:\Users\<PC Name>\AppData\Roaming\Mozilla\Firefox\Profiles\Local State`
- Opera: `C:\Users\<PC Name>\AppData\Roaming\Opera Software\Opera Stable\Local State`
- Brave: `C:\Users\<PC Name>\AppData\Local\BraveSoftware\Brave-Browser\User Data\Local State`

#### How does the Local State file look like?

```json
{
  "os_crypt": {
    "encrypted_key": "EncryptedKeyHere"
  }
}
```

### Decrypting Browser Passwords

Python scripts have emerged as indispensable tools for decrypting passwords stored by popular browsers like Google Chrome. These scripts typically entail a multifaceted approach:

- Extraction of the encryption key and encrypted passwords from browser files.
- In-depth comprehension of AES encryption mechanisms, utilizing the extracted key and IV for decryption.
- Implementation of sophisticated decryption algorithms to decode encrypted passwords effectively.

### Security Risks and Implications

While the educational value of decrypting browser passwords is undeniable, it also underscores the pressing security concerns. Malevolent actors could exploit these vulnerabilities to gain unauthorized access to sensitive user data, potentially precipitating grave privacy infringements and identity theft. Furthermore, the ease with which passwords can be decrypted underscores the critical need for robust password management practices and heightened vigilance on the part of both users and browser developers.

### Case Study: Decrypting Firefox Passwords

Drawing parallels with Chrome, Firefox employs encryption techniques to safeguard stored passwords. By deciphering the location of saved passwords and harnessing tools like the Network Security Services (NSS) library, users can decrypt Firefox passwords. However, this process also serves as a stark reminder of the inherent vulnerabilities permeating browser password management systems.

Heres an article on [How to Decrypt Firefox Passwords](https://medium.com/geekculture/how-to-hack-firefox-passwords-with-python-a394abf18016).

### Mitigating Risks and Enhancing Security

To address these vulnerabilities effectively, browser developers must proactively implement a slew of security measures, including:

- Adoption of stronger encryption algorithms and meticulous key management practices.
- Integration of enhanced user authentication mechanisms to thwart unauthorized access attempts.
- Advocacy for user education initiatives elucidating the criticality of password security and the adoption of robust password management tools.

### Conclusion

In summary, while browser password encryption epitomizes convenience, it's imperative to acknowledge the attendant security risks. By comprehensively dissecting the encryption methodologies employed by browsers like Chrome and Firefox, and meticulously scrutinizing the associated vulnerabilities, users can adopt a proactive stance toward safeguarding their digital assets. Moreover, it's incumbent upon browser developers to continually innovate and fortify security protocols, thereby ensuring a safer and more secure browsing environment for all users.

## Disclaimer

This script is intended for educational purposes only. The user is responsible for its use. The author assumes no responsibility for any misuse of this tool.

Author: [SOME-1HING](https://www.github.com/SOME-1HING)
