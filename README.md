# TDO_CS_02
Credential Stuffing Challenge Walkthrough - This project demonstrates the solution process for a Credential Stuffing cybersecurity challenge. The objective was to automate login attempts using a leaked credential dump, identify valid credentials, and retrieve the hidden flag from a remote banking service.

# Credential Stuffing Challenge Walkthrough

## Overview

This repository contains my solution and walkthrough for the **Credential Stuffing** challenge from a Capture The Flag (CTF) platform. The challenge demonstrates how attackers can use leaked username-password combinations to gain unauthorized access when users reuse credentials across multiple services.

The objective was to automate login attempts against a banking service using a provided credential dump and identify valid credentials that reveal the challenge flag.

---

## Challenge Description

Credential stuffing is a cyberattack technique where stolen credentials from previous data breaches are automatically tested against login portals. Since many users reuse passwords, attackers can often gain access to multiple accounts using the same credentials.

In this challenge:

- A credential dump file was provided.
- A Python script needed to be completed.
- The script connected to a remote banking service.
- Each username-password pair was tested automatically.
- The valid account returned the challenge flag.

---

## Methodology

### 1. Analyze the Source Code

The provided Python script:

- Connected to a remote server using sockets.
- Read usernames and passwords from a credential dump file.
- Sent login requests to the banking application.
- Checked server responses for successful authentication.

### 2. Parse the Credential Dump

The script reads the `creds-dump.txt` file and stores credentials in a dictionary:

```python
with open("creds-dump.txt", "r", encoding="utf-8") as f:
    for line in f:
        username, password = line.strip().split(";", 1)
        credentials[username] = password
```

### 3. Automate Login Attempts

Using Python's socket library:

```python
socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```

The script:

- Connects to the target host.
- Sends usernames.
- Sends passwords.
- Receives authentication responses.

### 4. Detect Successful Login

The script monitors server responses for the flag pattern:

```python
if b"picoCTF" in data4:
```

When a successful login occurs, the flag is saved locally.

### 5. Retrieve the Flag

After testing all credentials, one valid account successfully authenticated and returned the challenge flag.

---

## Skills Demonstrated

- Python Automation
- Socket Programming
- Credential Stuffing Concepts
- Network Communication
- CTF Methodology
- Authentication Testing
- Linux Command Line Usage

---

## Tools Used

- Python 3
- Linux WebShell
- Socket Library
- Text Processing
- CTF Platform

## Key Takeaways

- Password reuse significantly increases account compromise risk.
- Credential stuffing can be automated with simple scripting.
- Multi-factor authentication (MFA) greatly reduces credential stuffing effectiveness.
- Organizations should implement rate limiting, account lockouts, and anomaly detection to mitigate such attacks.

---

## Disclaimer

This project was completed in a controlled Capture The Flag (CTF) environment for educational and ethical cybersecurity purposes only.

Do not use these techniques against systems without explicit authorization.
