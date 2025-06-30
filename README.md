# Paranoid Qrypto: BTC Airgap Bridge

![Apache 2.0 License](https://img.shields.io/badge/License-Apache_2.0-ffd700.svg)
![Version](https://img.shields.io/badge/Version-1.0.0-informational.svg)
![Maintained](https://img.shields.io/badge/Maintained-Yes-green.svg)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

<p align="center">
  <img src="docs/logo.png" alt="Paranoid Qrypto Logo" width="128">
</p>

A 100% client-side, single-file HTML tool for securely managing the online parts of an air-gapped Bitcoin transaction workflow. This tool allows you to fetch live network data (like UTXOs and fee rates) and broadcast a signed transaction to the Bitcoin network without ever exposing your private keys to an online machine.

---

## Security-First Philosophy

This tool was built with a "paranoid" mindset, prioritizing security and transparency above all else.

*   **100% Client-Side:** All operations happen directly in your web browser. No data, keys, or transaction information is ever sent to any server, except for the final, signed transaction hex which is broadcast directly to public Bitcoin nodes.
*   **Works Completely Offline:** The tool is a single HTML file with no external dependencies. You can download it and run it on a completely air-gapped computer to generate QR codes from signed transaction data.
*   **Fully Auditable:** The entire source code is contained within a single, human-readable file. There are no hidden packages or compiled code. What you see is what you get.

## Cross-Platform Compatibility

As a self-contained HTML application, the BTC Airgap Bridge runs on any modern device with a standards-compliant web browser.

*   **Desktop:** Windows, macOS (Intel), macOS (Apple Silicon), Linux
*   **Android, iPhone, iPad:** Android OS, iOS / iPadOS
*   **Other devices:** E.g. Chromebook, Raspberry Pi, etc.
*   **Supported Browsers:** Works on all modern browsers, including Chrome, Firefox, Safari, Edge, and Brave.

### Requirements

*   **JavaScript must be enabled** in your browser for the tool to function.
*   For QR code scanning features, you must **grant the browser permission** to access your device's camera when prompted.

### Offline Functionality

The `index.html` file along with the libraries from the 'js' folder can be downloaded and run on a completely air-gapped machine. The following features will work perfectly offline:

*   ✅ **Generate QR Code**
*   ✅ **Regenerate QR Code**

Features that require a connection to the Bitcoin network, such as **Fetch UTXOs & Fees** and **Submit Signed TX**, will not function offline.

## Key Features

*   **Fetch UTXOs & Fees:** Safely get your account's Unspent Transaction Outputs (UTXOs) and recommended network fee rates from the live network to prepare for an offline transaction.
*   **Submit Signed Transaction:** Broadcast a signed raw transaction hex (pasted or scanned via QR code) to the Bitcoin network.
*   **Generate QR Code:** A general-purpose utility to create a QR code from any text or data, useful for moving a signed transaction hex from an offline machine.
*   **Regenerate QR Code:** A robust "lifesaver" utility that can decode blurry, low-quality, or difficult-to-read QR codes and regenerate them as clean, scannable images.

## How to Use: The Air-Gapped Workflow

This tool acts as the secure online interface for your offline cold wallet (like a hardware wallet or an offline computer running Sparrow/Electrum).

#### Step 1: On Your **Online** Machine

1.  Open the `index.html` file.
2.  Go to the **"Fetch UTXOs & Fees"** tab.
3.  Enter your public Bitcoin address (`bc1...`, `1...`, `3...`, etc.) and click "Fetch Account Info".
4.  Securely transfer the list of UTXOs and the current fee rates to your offline machine (e.g., by saving the data as a text file to a USB drive, or scanning a QR code).

#### Step 2: On Your **Offline** (Air-Gapped) Machine

1.  Using your preferred offline wallet software, construct your transaction.
2.  Import or use the UTXOs and fee rate you just transferred to build the transaction inputs and calculate the fee.
3.  Sign the transaction with your private key. This will produce a long hexadecimal string (the "signed raw transaction hex").
4.  Use a copy of this tool on your offline machine to turn the long transaction hex into a QR code using the "Generate QR" tab.

#### Step 3: Back on Your **Online** Machine

1.  Go to the **"Submit Signed TX"** tab.
2.  Either paste the hexadecimal hex directly into the text box or click **"Scan Signed TX QR"** to use your camera.
3.  Verify the network selection (Mainnet/Testnet) and click **"Submit Transaction"**.
4.  The tool will broadcast your transaction to the Bitcoin network and show you the final response.

---

## Dependencies & Verification

This tool is designed to be a secure, self-contained HTML file. It does not bundle a dedicated Bitcoin library. Instead, it interacts directly with trusted, public REST APIs for live network data and uses the following local libraries for QR code functionality.

To ensure transparency and allow for independent verification, the exact versions, source links, and SHA-256 file hashes are provided below.

### 1. jsQR.js

*   **Version:** `1.4.0`
*   **Purpose:** QR code decoding library used for scanning.
*   **Source of Truth (NPM):** [https://www.npmjs.com/package/jsqr/v/1.4.0](https://www.npmjs.com/package/jsqr/v/1.4.0)
*   **Direct Download Link:** [https://cdn.jsdelivr.net/npm/jsqr@1.4.0/dist/jsQR.js](https://cdn.jsdelivr.net/npm/jsqr@1.4.0/dist/jsQR.js)
*   **SHA-256 Hash:** `aec81b459d4e3856885fca04b497474227396ab793daedf402fd80f7b9fcc337`

### 2. qrcode.min.js

*   **Version:** `1.0.0`
*   **Purpose:** QR code generation library.
*   **Source of Truth (Github):** [https://github.com/davidshimjs/qrcodejs](https://github.com/davidshimjs/qrcodejs)
*   **Direct Download Link:** [https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js](https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js)
*   **SHA-256 Hash:** `c541ef06327885a8415bca8df6071e14189b4855336def4f36db54bde8484f36`

---

## License

This project is licensed under the **Apache License 2.0**. Please see the `LICENSE` file for full details. A `NOTICE` file is also included for attribution purposes.

## Disclaimer

This tool is provided "AS IS", WITHOUT WARRANTY OF ANY KIND, either express or implied. The user assumes all risks associated with its use. Always verify critical information and test with small amounts before performing significant transactions.

## Bug Reports & Feedback

If you find a bug or have a feature request, please open an issue on the [GitHub Issues page](https://github.com/paranoid-qrypto/btc-airgap-bridge/issues).
