# Data Protection and Information Security

## Project Overview
This project explores fundamental data protection mechanisms, cryptography concepts, full disk encryption, file-level access controls, and steganography detection techniques. The objective is to understand how data confidentiality, integrity, and privacy are maintained across operating system layers and how to defend against stealthy exfiltration methods.

---

## Tools & Technologies Used

* **Microsoft BitLocker (`manage-bde`):** Used for configuring and verifying Full Disk Encryption (FDE) and TPM key protection on Windows OS.
* **Encrypted File System (EFS):** Utilized for granular file- and directory-level security controls.
* **Steganography Online Utility ([stylesuxx.github.io/steganography](https://stylesuxx.github.io/steganography/)):** Web-based tool used to analyze payload embedding, binary image transformations, and visual artifact changes[cite: 1, 2].
* **Windows Command Prompt / Administrator Terminal:** Executed system-level administration commands to inspect volume encryption and key management[cite: 3].

---
## Core Techniques & Objectives

| Technique | Purpose | Implementation Context |
| :--- | :--- | :--- |
| **Encryption** | Ensures confidentiality by making information unreadable without the appropriate key. | Standard cryptographic algorithms. |
| **Full Disk Encryption (FDE)** | Protects data at rest across physical storage media. | Microsoft BitLocker utilizing a Trusted Platform Module (TPM) chip[cite: 3]. |
| **Encrypted File System (EFS)** | Provides granular file- and folder-level protection. | Windows EFS utility. |
| **Steganography** | Conceals the literal existence of sensitive data within carrier files[cite: 1, 2]. | Web-based steganography testing tools[cite: 1, 2]. |

---

## Key Findings
* **Encryption vs. Steganography:** Encryption alters information to make it unreadable without the correct key, whereas steganography conceals the existence of the information entirely by embedding it inside another file type, such as an image or audio clip[cite: 1, 2].
* **Threat Actor TTPs:** Threat actors frequently leverage steganography to exfiltrate sensitive data covertly, hiding payloads inside everyday media formats from which they can later be retrieved[cite: 1, 2].

---

## Key Takeaways & Best Practices
* **Detection Challenges:** Files modified via steganography often retain the exact same physical appearance before and after embedding. Best practice requires comparing cryptographic hashes of the file or analyzing unexpected file size discrepancies.
* **Insider Threat Vector:** Steganography is a serious, hard-to-trace security concern that is frequently carried out by insider threat actors.
* **Disk Security Hardening:** Full Disk Encryption solutions like BitLocker rely on hardware components like a TPM chip, but should always be paired with strong user passwords to protect data if physical hardware is lost or stolen[cite: 3].

---

## Visual Evidence & Lab Artifacts

### 1. Full Disk Encryption Verification (BitLocker)
Command-line execution confirming 100% volume encryption, active protection status, and TPM/Numerical Password key protectors[cite: 3]:
```cmd
C:\Windows\System32> manage-bde -status
