# Cipher BSK Web — JavaScript Text Encryption and Decryption

**Cipher BSK Web (BSK Online)** is a browser-based JavaScript application of **Cipher BSK — Bornomala Symmetric Key**, originally implemented in C++. Developed by **Sazzad Hossain Saju**, it makes the cipher easy to access and experiment with: enter text and a key, then encrypt or decrypt without installing a console application.

**[Open the live application](https://sazzad-saju.github.io/BSK-Online/) · [Read the project story on Medium](https://medium.com/@sham3r/cipher-bsk-from-a-simple-experiment-to-practical-solutions-my-passionate-journey-in-cryptography-d5de4e83add5)**

## Research Foundation

The cipher model is documented in **[A Hybrid Cryptographic Scheme of Modified Vigenère Cipher using Randomized Approach for Enhancing Data Security](https://www.ijcaonline.org/archives/volume183/number2/31897-2021921290/)**.

- **Authors:** Sazzad Hossain Saju, Sayed Mahmudul Haque, and Liakot Hossain Lingcon.
- **Publication:** *International Journal of Computer Applications*, 183(2), 1–8, May 2021.
- **DOI:** [10.5120/ijca2021921290](https://doi.org/10.5120/ijca2021921290).
- **Discovery:** [Find the paper on Google Scholar](https://scholar.google.com/scholar?q=A+Hybrid+Cryptographic+Scheme+of+Modified+Vigenere+Cipher+using+Randomized+Approach+for+Enhancing+Data+Security).

The wider hybrid cryptosystem combines Cipher BSK for message encryption with RSA for encrypting the symmetric key. **This application implements the symmetric Cipher BSK text tool.** RSA key exchange and the planned image-steganography workflow are separate from this website.

## What It Does

- Encrypts text using the JavaScript Cipher BSK implementation.
- Decrypts ciphertext back into text using the original key.
- Replaces the text in the same box after each operation.
- Allows repeated encryption of the previous result for multiple rounds.
- Provides a copy control after encryption.
- Performs the cipher calculations locally in the browser, with no account or server-side vault.

The application is hosted on **GitHub Pages** at <https://sazzad-saju.github.io/BSK-Online/>.

## How to Use

### Encrypt

1. Open the live application.
2. Enter your text in the plaintext/ciphertext box. Start with a short, single-line ASCII example.
3. Type a key in the key box.
4. Click **Encrypt** once and wait for the result.
5. Copy and save the ciphertext, keeping the key separately.

### Decrypt

1. Paste the complete ciphertext into the text box.
2. Type the same key used for encryption.
3. Click **Decrypt** and wait for the recovered text.

Both operations replace the current box contents. Reloading or leaving the page loses any unsaved result. There is no key-recovery feature.

### Key Requirements

The JavaScript interface accepts a key with:

- At least eight characters.
- At least one letter and one digit.
- Only letters, digits, and the symbols `@ $ ! % * # ? &`.
- No spaces.

These rules describe this web interface and differ from the original C++ console application's validation. They are not a guarantee of key strength.

### Multiple Encryption Rounds

After encrypting, click **Encrypt** again to encrypt the ciphertext currently in the box. To recover the original text, decrypt the same number of times.

If you use different keys, reverse their order when decrypting:

```text
Encrypt with key A → encrypt the result with key B
Decrypt with key B → decrypt the result with key A → original text
```

Record the round count and key order. Repeated rounds increase the text size and do not by themselves establish stronger security.

### Browser Performance

Calculations run synchronously in the browser. Large inputs, many encryption rounds, or rapid repeated clicks can make the tab unresponsive. Wait for each operation to finish, avoid clicking repeatedly, and experiment with small inputs first.

## Running Locally

Download or clone the repository and serve it as a static website. For example, with Python 3 installed, run this from the repository directory:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/>. There is no build step or backend application. The page uses external Bootstrap and Font Awesome assets, so the complete visual interface depends on those providers being reachable. Clipboard access also depends on browser permissions and support.

## Source Layout

| File | Purpose |
| --- | --- |
| `index.html` | Page interface, research background, usage notes, and FAQ. |
| `css/BSK.css` | Application styling. |
| `js/keyGen.js` | Key generation and pseudorandom helpers. |
| `js/encrypt.js` | Cipher BSK encryption and output formatting. |
| `js/decrypt.js` | Ciphertext normalization and decryption. |
| `js/BSK.js` | Form validation, button actions, and copying results. |
| `img/` | Logo and image assets. |
| `file/` | Original downloadable console application. |

## Scope and Compatibility

Cipher BSK is an experimental research cipher. This demonstration is intended for learning and code exploration; publication and successful round trips are not independent security validation. It does not implement ciphertext authentication or provide a password-manager vault.

The browser implementation is designed around character-value transformations. Exact recovery of Unicode, line breaks, and arbitrary binary data is not supported by this demonstration; use short, single-line ASCII examples.

The JavaScript and original C++ implementations use different pseudorandom-generation behavior. Do not assume their ciphertext formats are interchangeable: decrypt with the implementation that produced the ciphertext.

The application's cipher handlers do not upload your text or key or persist a history. However, the website loads external styles, scripts, and icons; local calculation does not mean that the page makes no network requests.

## Cite the Research

If you use or build on this model in your research, please cite the original paper:

> Saju, S. H., Haque, S. M., and Lingcon, L. H. (2021). A Hybrid Cryptographic Scheme of Modified Vigenère Cipher using Randomized Approach for Enhancing Data Security. *International Journal of Computer Applications*, 183(2), 1–8. https://doi.org/10.5120/ijca2021921290

```bibtex
@article{saju2021hybrid,
  author  = {Sazzad Hossain Saju and Sayed Mahmudul Haque and Liakot Hossain Lingcon},
  title   = {A Hybrid Cryptographic Scheme of Modified Vigen{\`e}re Cipher using Randomized Approach for Enhancing Data Security},
  journal = {International Journal of Computer Applications},
  volume  = {183},
  number  = {2},
  pages   = {1--8},
  year    = {2021},
  doi     = {10.5120/ijca2021921290}
}
```

## Explore the Ecosystem

- [Original Cipher BSK C++ console application](https://github.com/Sazzad-Saju/BSK-Stream-Cipher).
- [RSA public-key component in Python](https://github.com/Sazzad-Saju/RSA_Algorithm).
- [Cipher BSK JavaScript npm package](https://github.com/Sazzad-Saju/cipher-bsk-npm-package).
- [Cipher BSK PHP and Laravel package](https://packagist.org/packages/sham3r/cipher-bsk).
- [The story behind the research and open-source tools](https://medium.com/@sham3r/cipher-bsk-from-a-simple-experiment-to-practical-solutions-my-passionate-journey-in-cryptography-d5de4e83add5).
