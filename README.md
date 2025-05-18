# SMS Bomber ReZNuM 🚀

![Python](https://img.shields.io/badge/python-3.6%2B-blue)
![Issues](https://img.shields.io/github/issues/ItsReZNuM/SMS_Bomber)
![Stars](https://img.shields.io/github/stars/ItsReZNuM/SMS_Bomber?style=social)
![Forks](https://img.shields.io/github/forks/ItsReZNuM/SMS_Bomber?style=social)
![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen)

Welcome to **SMS Bomber ReZNuM**, a Python-based script designed to demonstrate the interaction with various Iranian web service APIs for sending SMS verification codes. This project is intended for **educational purposes** and **penetration testing** (with explicit permission) to explore HTTP requests, multithreading, and API interactions. 🚨 **Use responsibly and legally!**

## 📖 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Installation](#-installation)
- [Usage](#-usage)
- [Supported Services](#-supported-services)
- [How It Works](#-how-it-works)
- [Contributing](#-contributing)
- [Code of Conduct](#-code-of-conduct)
- [License](#-license)
- [Disclaimer](#-disclaimer)
- [Contact](#-contact)

## 🌟 About the Project

**SMS Bomber ReZNuM** is a Python script that automates sending SMS verification codes to a specified phone number by leveraging the APIs of multiple Iranian web services. It showcases advanced Python programming concepts such as:

- **HTTP Requests**: Using the `requests` library to interact with APIs.
- **Multithreading**: Utilizing `threading` for parallel execution.
- **Error Handling**: Robust try-except blocks to manage network issues.
- **Input Validation**: Phone number standardization with regex.

## ⚠️ Warning

**This tool is for educational and authorized testing purposes only. Unauthorized use may violate laws and terms of service of targeted services. See the [Disclaimer](#-disclaimer) for details.**

## 🎯 Goals

- Educate users on API interactions and HTTP request handling.
- Demonstrate multithreading for performance optimization.
- Provide a framework for authorized security testing of SMS-based systems.

## ✨ Features

| **Feature** | **Description** |
|-------------|-----------------|
| Multi-Service Support | Sends SMS via 40+ Iranian services like Snapp, Divar, and Alibaba. |
| Multithreading | Executes requests in parallel for faster performance. |
| Phone Validation | Validates and standardizes phone numbers using regex. |
| Customizable Delay | Allows users to set delays between requests (default: 0.1s). |
| Error Resilience | Handles network errors gracefully with try-except blocks. |
| Dependency Management | Automatically installs required libraries (`requests`, `urllib3`). |
| Console Feedback | Color-coded output for success/failure of SMS requests. |

## 🛠 Installation

**Prerequisites**

- **Python 3.6+** installed on your system.
- A compatible OS (Windows, macOS, Linux).
- Internet connection for API requests.

**Steps**

1. **Clone the Repository**:

   ```
   git clone https://github.com/ItsReZNuM/SMS_Bomber.git
   cd SMS_Bomber
   ```

2. **Install Dependencies**:

   Install the required libraries listed in `requirements.txt`:

   ```
   pip install -r requirements.txt
   ```

   **Note**: The script also attempts to install `requests` and `urllib3` automatically if they're missing.

3. **Verify Setup**:

   Ensure Python is installed:

   ```
   python --version
   ```

## 🚀 Usage

1. **Run the Script**:

   ```
   python Bomber.py
   ```

2. **Enter Phone Number**:

   - Input a phone number in formats like `+989123456789`, `989123456789`, `09123456789`, or `9123456789`.
   - The script validates and standardizes the input.

3. **Set Delay (Optional)**:

   - Specify the delay between requests (in seconds). Press Enter for default (0.1s).

4. **Observe Output**:

   - The script sends SMS requests to supported services and displays results:

     ```python
     (Snapp) Code Was Sent
     (Divar) Code Was Sent
     [-] Error TimeOut
     ```

5. **Stop the Script**:

   - Press `Ctrl+C` to exit (`User Exited` message displayed).

**Example**

```
$ python Bomber.py
```
```python
Termux Script

Info:
    [+] Instagram Channel: @reznum 
    [+] Telegram Channel: @ReZNuM

system:
    [+] Platform: Linux
    [+] Node: my-machine
    [+] Release: 5.15.0

[?] Enter Phone Number (+98) - +989123456789
[?] Enter Sleep Time Between Requests [Default=0.1] - 0.2
(Snapp) Code Was Sent
(Gap) Code Was Sent
...
```

## 📋 Supported Services

The script interacts with the following Iranian services (as of the latest version):

| **Service** | **API Endpoint** | **Notes** |
|-------------|------------------|-----------|
| Snapp | `https://app.snapp.taxi/api/api-passenger-oauth/v2/otp` | Taxi service |
| Divar | `https://api.divar.ir/v5/auth/authenticate` | Classified ads |
| Tap30 | `https://tap33.me/api/v2/user` | Ride-hailing |
| Snapfood | `https://snappfood.ir/mobile/v2/user/loginMobileWithNoPass` | Food delivery |
| Alibaba | `https://ws.alibaba.ir/api/v3/account/mobile/otp` | Travel booking |
| Sheypoor | `https://www.sheypoor.com/auth` | Classified ads |
| Torob | `https://api.torob.com/a/phone/send-pin/` | Price comparison |
| SnappMarket | `https://api.snapp.market/mart/v1/user/loginMobileWithNoPass` | Online supermarket |
| Filmnet | `https://api-v2.filmnet.ir/access-token/users/` | Streaming service |
| DrDr | `https://drdr.ir/api/registerEnrollment/sendDisposableCode` | Medical consultation |
| ... | ... | 40+ services supported |

**Note**: API endpoints may change, rendering some services inaccessible. Open an issue if you encounter failures.

## 🔍 How It Works

**Workflow**

1. **Input Processing**:

   - The `is_phone` function validates and standardizes the phone number using regex.
   - Example: `09123456789` → `+989123456789`.

2. **Service Requests**:

   - Each service has a dedicated function (e.g., `snap`, `divar`) that sends an HTTP POST/GET request to the service's API.
   - Headers mimic a legitimate browser request (e.g., `User-Agent`, `Origin`).
   - Data includes the phone number in the required format (JSON or URL-encoded).

3. **Multithreading**:

   - The `Vip` function spawns threads for each service using `threading.Thread`.
   - A user-defined delay (`Time`) is applied between thread launches.

4. **Error Handling**:

   - Network errors (e.g., timeouts) are caught and ignored, ensuring the script continues running.
   - Success is confirmed via API response codes or specific JSON fields.

5. **Looping**:

   - The script runs indefinitely until interrupted, sending SMS in cycles.

**Technical Details**

- **Libraries**: `requests`, `urllib3`, `threading`, `re`, `time`, `os`, `platform`.
- **HTTP Methods**: Primarily POST, some GET requests.
- **SSL Handling**: SSL warnings disabled for compatibility (`urllib3.disable_warnings()`).
- **Console Output**: Uses ANSI color codes for visual feedback.

## 🤝 Contributing

We welcome contributions to enhance **SMS Bomber ReZNuM**! Here's how you can help:

**How to Contribute**

1. **Fork the Repository**: Click the "Fork" button at the top-right of the GitHub page.

2. **Clone Your Fork**:

   ```
   git clone https://github.com/your-username/SMS_Bomber.git
   ```

3. **Create a Branch**:

   ```
   git checkout -b feature/your-feature-name
   ```

4. **Make Changes**:

   - Add new services, improve error handling, or fix bugs.
   - Follow the [Code Style](#code-style).

5. **Commit Changes**:

   ```
   git commit -m "Add feature: your feature description"
   ```

6. **Push to Your Fork**:

   ```
   git push origin feature/your-feature-name
   ```

7. **Open a Pull Request**:

   - Go to the original repository and submit a PR with a detailed description.

**Code Style**

- Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) guidelines.
- Use descriptive variable names (e.g., `snap_headers` instead of `snapH`).
- Comment complex logic for clarity.

**Ideas for Contributions**

- Add new service APIs.
- Implement rate-limiting controls.
- Enhance error logging.
- Add unit tests using `pytest`.

## 📜 Code of Conduct

We are committed to fostering an inclusive and respectful community. Please adhere to our [Code of Conduct](CODE_OF_CONDUCT.md) in all interactions.


## ⚠️ Disclaimer

**SMS Bomber ReZNuM** is provided for **educational and authorized testing purposes only**. The developers are not responsible for any misuse or illegal activities conducted with this tool. Unauthorized use, such as sending unsolicited SMS or violating service terms, may result in legal consequences. **Use at your own risk**.

## 📬 Contact

Have questions or suggestions? Reach out!

- **GitHub Issues**: Open an issue for bugs or feature requests.
- **Instagram**: [@rez.num](https://instagram.com/rez.num)
- **Telegram**: [@ItsReZNuM](https://t.me/ItsReZNuM)

---

⭐ **Star this repository** if you found it useful!  
🙌 Contributions and feedback are greatly appreciated!

---

<p align="center">
  Made with ❤️ By ReZNuM
</p>