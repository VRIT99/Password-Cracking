# Password-Cracking
Network Walk's Week 3 Project
# Week 3 — Password Cracking Fundamentals

**NetworkWalks Cybersecurity Program**

## 📋 Overview

This project documents my work for Week 3 of the NetworkWalks Cybersecurity Program, focused on password cracking techniques used in penetration testing and security assessments. The objective was to understand how password-protected files can be compromised using dictionary-based attacks, and why weak password practices pose a significant security risk.

## 🎯 Objectives

- **W3-PM1:** Password Cracking with John the Ripper (JTR)
- **W3-PM2:** Password Cracking with NetworkWalks Tools

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| John the Ripper (JTR) | Offline password cracking utility |
| `pdf2john.pl` | Script to extract crackable hash from password-protected PDFs |
| rockyou.txt | Wordlist containing leaked/common passwords, used for dictionary attacks |
| NetworkWalks Password Cracker | Browser-based password cracking tool |
| Kali Linux | Operating system / testing environment |

## 🔍 Methodology

### Part 1: Password Cracking with John the Ripper

1. **Hash Extraction**
   Used `pdf2john.pl` to extract the password hash from each password-protected PDF file:
```bash
   perl /usr/share/john/pdf2john.pl "target.pdf" > hash.txt
```

2. **Dictionary Attack**
   Ran John the Ripper against the extracted hash using the rockyou.txt wordlist:
```bash
   john --wordlist=/usr/share/seclists/Passwords/Leaked-Databases/rockyou.txt hash.txt
```

3. **Result Verification**
   Displayed the cracked password using:
```bash
   john --show --format=PDF hash.txt
```

**Passwords successfully cracked:**

| File | Cracked Password | Time Taken |
|------|-------------------|------------|
| My Locked PDF1.pdf | `good-luck` | 7 seconds |
| My Locked PDF2.pdf | `password1` | < 1 second |
| My Locked PDF3.pdf | `1qaz2wsx` | < 1 second |

### Part 2: Password Cracking with NetworkWalks Tools

As a comparative exercise, the same PDF files were tested using NetworkWalks' in-browser password cracking tool, which uses a similar dictionary-based approach without requiring command-line access. This provided a useful comparison between CLI-based and GUI/web-based cracking workflows.

## 📊 Key Findings

- All test passwords were cracked within seconds, highlighting how vulnerable common/weak passwords are to dictionary attacks.
- The rockyou.txt wordlist remains highly effective because it is built from real-world leaked password databases, meaning many users still reuse these exact passwords.
- The comparison between JTR (CLI) and NetworkWalks Cracker (browser-based) showed that both approaches achieve the same outcome, differing mainly in accessibility and use case — CLI tools offer more flexibility for advanced use cases, while browser tools are quicker for simple, single-file checks.

## 🔐 Security Takeaways

This exercise reinforced a few important lessons from a defensive security perspective:

1. **Weak passwords remain one of the most common attack vectors.** Encryption strength does not matter if the underlying password is easily guessable.
2. **Dictionary attacks are highly effective and low-effort** for attackers when users choose common or reused passwords.
3. **Strong password policies and MFA (Multi-Factor Authentication)** are essential controls that organizations should enforce to mitigate this risk.
4. Understanding these attack techniques is valuable not just offensively, but also for building better defensive strategies during VAPT engagements.

## 📁 Repository Contents
