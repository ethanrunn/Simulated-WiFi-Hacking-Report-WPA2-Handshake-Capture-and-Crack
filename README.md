# 🛠️ Simulated WiFi Hacking Report: WPA2 Handshake Capture and Crack

## 📌 Objective

To ethically demonstrate a **WPA2 WiFi password crack** using a publicly available `.cap` file and a dictionary-based brute-force approach, without the use of any physical router or real-world WiFi network.

---

## 🧪 Lab Setup

### ⚙️ Tools Used

* **Kali Linux** (VM)
* **Aircrack-ng 1.7**
* **Wireshark**
* **rockyou.txt** (Kali default wordlist)

### 🧾 Files Used

* **Capture File:** `wpa.full.cap` (downloaded from [Aircrack-ng’s official site](https://www.aircrack-ng.org/doku.php?id=wpa_capture))
* **Wordlist:** `/usr/share/wordlists/rockyou.txt`

---

## 🔍 Process and Steps

### ✅ Step 1: Analyzing the `.cap` File

* The capture file contains a **WPA2 handshake** from a simulated access point.
* Opened the file in **Wireshark** and applied the filter `eapol` to locate handshake packets.
* Identified the **BSSID** of the access point (via Transmitter/BSSID field).

### ✅ Step 2: Cracking the Password with Aircrack-ng

```bash
sudo aircrack-ng -w /usr/share/wordlists/rockyou.txt -b [BSSID] wpa.full.cap
```

* Replaced `[BSSID]` with the value obtained from Wireshark.
* Aircrack-ng ran the brute-force attack using the provided dictionary.
* **Success:** Password was found — `444445555`.

> 🖼️ See Screenshot:
> ![Aircrack-ng Result](./Screenshot_2025-05-23_15_18_59.png)

---

## 📸 Evidence Collected

| Item                 | Details        |
| -------------------- | -------------- |
| WPA2 Handshake File  | `wpa.full.cap` |
| Password Cracked     | `444445555`    |
| Cracking Tool        | `Aircrack-ng`  |
| Wordlist Used        | `rockyou.txt`  |
| BSSID Extracted With | `Wireshark`    |
| Screenshot           | Included above |

---

## 🛡️ Mitigation Recommendations

To prevent this kind of WiFi attack in real environments:

1. **Use WPA3:** Stronger encryption and protections against dictionary attacks.
2. **Set Strong Passwords:** Use long, complex, non-dictionary-based passphrases.
3. **Disable WPS (Wi-Fi Protected Setup):** Commonly exploited in brute-force attacks.
4. **MAC Filtering:** Restrict device access based on MAC addresses.
5. **Segment Your Network:** Keep critical devices (e.g., CCTV, servers) on separate VLANs.
6. **Regularly Update Firmware:** Keep your router’s firmware patched and up to date.

---

## ⚠️ Ethical Consideration

This exercise was conducted in a fully controlled **lab environment** using public capture files. No real network was targeted or accessed. This simulation is strictly for educational purposes and security awareness.

---

Let me know if you'd like this exported to a PDF or Markdown file for GitHub upload.
