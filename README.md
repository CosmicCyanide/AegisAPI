
# AegisAPI

AegisAPI is an advanced API security analyzer that combines powerful fuzzing, rate-limiting tests, anomaly detection, and JWT cracking simulations into one comprehensive tool. It is designed to help developers, penetration testers, and security researchers analyze and secure their APIs with a modern and beautiful interface.

## Features

- **Advanced Fuzzing**: Supports SQLi, XSS, Command Injection, and File Inclusion attacks using custom payloads.
- **JWT Cracking**: Simulates cracking JWT tokens with weak keys (supports custom key files such as rockyou).
- **Rate Limiting & DoS Simulation**: Tests rate limits by sending bursts of requests and can simulate Denial of Service attacks.
- **Anomaly Detection**: Machine learning-based detection of slow or unusual API response times.
- **Entropy Analysis**: Detects sensitive data exposure by analyzing the entropy of API responses.
- **API Key Rotation**: Automatically tests the rotation of API keys and checks for validity.
- **Dynamic Animations**: Includes beautiful real-time terminal animations and progress indicators for long-running tasks.
- **JSON-based Configuration**: Easily configure API details, attack settings, weak keys, and more using an external JSON configuration file.
- **Comprehensive Reporting**: Generates JSON reports of all tests, including endpoints, vulnerabilities, and anomalies detected.

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/aegisapi.git
   cd aegisapi

    Install the required dependencies:

    pip install -r requirements.txt

    Set up your config.json file (example provided below).

Configuration

AegisAPI uses a JSON configuration file (config.json) to load settings, making it easy to modify attack parameters without editing the code. Below is an example of a basic configuration:

json

{
  "api_base_url": "https://api.example.com",
  "swagger_url": "https://api.example.com/swagger.json",
  "auth_token": "YOUR_JWT_HERE",
  "rate_limit_requests": 500,
  "burst_size": 50,
  "sequential_delay": 0.3,
  "adaptive_threshold": 300,
  "slow_threshold_ms": 1000,
  "jwt_cracking": true,
  "use_key_list": true,
  "weak_key_file": "rockyou.txt",
  "fuzzing_types": ["SQLi", "XSS", "Command Injection"],
  "port_scan_range": "80-1000",
  "entropy_threshold": 4.5,
  "enable_dos_attack": true,
  "dos_attack_duration": 60
}

Usage

After setting up your config.json, you can run AegisAPI directly:

bash

python aegisapi.py

Options

    Fuzzing: AegisAPI will automatically fuzz all API endpoints using the payloads defined in the config.json. Each fuzzing type (SQLi, XSS, Command Injection) will be tested on each endpoint.

    Rate Limiting: The tool simulates multiple requests (up to 500 by default) to test API rate limits. The number of requests and burst size can be customized in the config.

    JWT Cracking: If enabled, AegisAPI will attempt to crack the JWT token using a list of weak keys (such as rockyou.txt or a custom key list).

    Anomaly Detection: Using machine learning (Isolation Forest), the tool will analyze API response times and flag anomalies.

    DoS Attack: AegisAPI simulates a Denial of Service attack on the API by sending a flood of requests. The duration and request intensity can be configured.

Reporting

AegisAPI generates a detailed JSON report after running the analysis. The report includes:

    List of API endpoints tested
    Vulnerabilities detected during fuzzing (e.g., SQLi, XSS)
    JWT cracking results (e.g., cracked keys)
    Rate limiting results (e.g., rate limit trigger points)
    Anomalies detected via response time analysis

The report is saved as super_advanced_security_report.json by default, but this can be modified in the configuration.
Example Report

json

[
    {
        "time": "2024-09-20 18:45:33",
        "endpoint": "https://api.example.com/v1/user",
        "status": "Rate Limit Triggered"
    },
    {
        "time": "2024-09-20 18:46:12",
        "endpoint": "https://api.example.com/v1/user",
        "status": "SQLi Vulnerability Detected",
        "payload": "' OR 1=1 --"
    }
]

Visualization

AegisAPI includes advanced real-time terminal animations and visualizations. Progress bars, spinning indicators, and live status updates ensure that you have a dynamic view of the tool's operations.
Advanced Features

    Port Scanning: Performs a port scan on the host to check for open ports in a specified range.
    Key Rotation Simulation: Simulates the rotation of API keys by testing multiple keys from an external file.
    Data Encryption: Supports data encryption using PBKDF2 for secure data storage and communication testing.
    Entropy Monitoring: Detects high-entropy data, indicating possible encrypted or sensitive information leakage.
    Dynamic Rate Adaptation: Automatically adjusts the request rate during fuzzing based on response times.

Requirements

    Python 3.x
    Libraries (included in requirements.txt):
        requests
        jwt
        psutil
        termcolor
        rich
        tqdm
        matplotlib
        scikit-learn
        pyfiglet
        colorama
        concurrent.futures
        tabulate

License

This project is licensed under the MIT License. See the LICENSE file for details.
