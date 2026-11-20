# Week 3 – Password Cracking with JTR & NetworkWalks Tools

Cybersecurity & Ethical Hacking course project — **Week 3, Project Modules 1 & 2** (NetworkWalks Academy).

The task was to recover the password of a locked PDF file using two different methods:

1. **John the Ripper (JTR) + Johnny GUI** — the industry-standard offline password-cracking tool.
2. **NetworkWalks Hash Calculator + Password Cracker** — free browser-based tools that do the same job without installing anything.

> ⚠️ **Educational use only.** These PDFs were deliberately created with weak, known-pattern passwords for a training lab. The techniques below (`pdf2john` / hash extraction + dictionary attack) should only ever be used on files you own or are explicitly authorized to test.

---

## 🧰 Tools Used

| Tool | Purpose |
|---|---|
| [John the Ripper (JTR)](https://www.openwall.com/john/) | Core password-cracking engine (CLI) |
| [Johnny](https://openwall.info/wiki/john/johnny) | GUI front-end for John the Ripper |
| [Online Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) | Converts a locked PDF into a crackable `$pdf$...` hash (pdf2john equivalent) |
| [NetworkWalks Hash Calculator](https://networkwalks.com/hash-calculator/) | Browser-based PDF → hash extractor |
| [NetworkWalks Password Cracker](https://networkwalks.com/password-cracker/) | Browser-based dictionary attack against a `$pdf$` hash |

---

## 🔑 Module 1 — Cracking with John the Ripper / Johnny

**Steps performed:**

1. Downloaded John the Ripper (jumbo build) and the Johnny GUI for Windows.
2. Installed Johnny and pointed it at `john.exe` under **Settings → John the Ripper executable**.
3. Uploaded the locked PDF to the online PDF hash extractor to generate a `pdf2john`-style hash.
4. Copied the hash (starting with `$pdf$...`) into a text file.
5. Opened the hash file in Johnny via **Open password file**.
6. Clicked **Start new attack** and let Johnny/John run its wordlist attack.
7. John recovered the password (`password1`) and displayed it in the Passwords tab.
8. Opened the PDF in Adobe Acrobat Reader using the recovered password — file unlocked, flag captured.

### Extracted hash (`my_hash_1.txt`)
```
$pdf$4*4*128*-1028*1*16*ca7f72f11459cba469f1005a8765ed51*32*f32d8fa1bfbe2648226dffc39f7909ea0021446990b9e4114071a4d9104984c1*32*9322f50c29569712067a775264635e4954ccb1b99e209d664984054ffad30a6a
```

**Cracked password:** `password1`
**Flag captured:** `nw{networkwalks_flag1_jtr_270521_1}`

📸 Screenshot — PDF unlocked after JTR/Johnny attack:
![Flag 1 — cracked with JTR/Johnny](screenshots/flag4_NWTools_PDF1.png)

---

## 🔑 Module 2 — Cracking with NetworkWalks Hash Calculator & Password Cracker

**Steps performed:**

1. Downloaded the locked PDF (`My Locked PDF1.pdf`) from the lab page.
2. Opened the **NetworkWalks Hash Calculator** (`networkwalks.com/hash-calculator`) in the browser.
3. Uploaded the PDF under the **PDF** tab — the tool parsed it locally and returned a crackable `$pdf$...` hash (no file ever leaves the browser).
4. Copied the full hash value.
5. Opened the **NetworkWalks Password Cracker** (`networkwalks.com/password-cracker`).
6. Pasted the hash and ran the attack using the built-in 100-word dictionary.
7. Tool matched the password after trying several candidates and displayed: `PASSWORD CRACKED SUCCESSFULLY → password1`.
8. Opened the locked PDF in Adobe Acrobat Reader with `password1` — file unlocked, flag captured.

### Extracted hashes (supporting files used in testing)

**`hash_3.txt`**
```
$pdf$4*4*128*-1028*1*16*0853f2cde0ef15b1c0f93ed229d3b1ad*32*8f13ce5aa39ad974364d36a057da76790021446990b9e4114071a4d9104984c1*32*ceecdac74b19b5a62688d3b3524e1374c955cbb9cc3c45316494d9446ef81af1
```

**`hash4.txt`**
```
$pdf$4*4*128*-1028*1*16*34eb542eff4e1b0b32d25ce15a9a7281*32*b77872bfc9a24fb2f845066283a8fc1b0021446990b9e4114071a4d9104984c1*32*e7572256e4b552cd57988f5134214b91920d94d7a6bf550ea94a2995c7f2ab02
```

**`my_hash_2.txt`**
```
$pdf$4*4*128*-1060*1*16*55d1a5c14175da449753199e44971d32*32*777fd021a7f3c5ae598c0c6495c7f76e00000000000000000000000000000000*32*ceecdac74b19b5a62688d3b3524e1374c955cbb9cc3c45316494d9446ef81af1
```

**Cracked password:** `password1`

📸 Screenshots — additional flags captured during the lab:

| Screenshot | Result |
|---|---|
| ![Flag — My Locked PDF1](screenshots/flag1_PDF1.png) | `nw{cybersecurity_flag_captured_2608}` |
| ![Flag — My Locked PDF2](screenshots/flag2_PDF2.png) | `nw{networkwalks_persistence_jtr_270521}` |
| ![Flag — My Locked PDF3](screenshots/flag3_PDF3.png) | `nw{networkwalks_flag_260821_1}` |

---

## 🏁 Flags Captured

| # | Source file | Flag |
|---|---|---|
| 1 | My Locked PDF1.pdf (JTR/Johnny) | `nw{cybersecurity_flag_captured_2608}` |
| 2 | My Locked PDF2.pdf | `nw{networkwalks_persistence_jtr_270521}` |
| 3 | My Locked PDF3.pdf | `nw{networkwalks_flag_260821_1}` |
| 4 | My Locked PDF1.pdf (NetworkWalks Tools) | [my_hash_1.txt](https://github.com/user-attachments/files/35168188/my_hash_1.txt)

networkwalks_flag1_jtr_270521_1}` |
*Course: Cybersecurity & Ethical Hacking — Week 3 Project Work (NetworkWalks Academy) · [networkwalks.com](https://www.networkwalks.com)*
[README.md](https://github.com/user-attachments/files/35167982/README.md)






