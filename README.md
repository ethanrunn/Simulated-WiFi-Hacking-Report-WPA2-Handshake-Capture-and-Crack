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

This task involved using a wifi router to initiate a wireless connection and then capturing the traffic and WPA2 handshake using Wireshark. I didn’t have a physical router, so I “simulated” by going to Aircrack-ng’s official website and downloading a .cap file that had captured a WPA2 handshake (wpa.full.cap).

Opened up the file in Wireshark and applied the filter “eapol” to locate handshake packets. Identified the BSSID of the access point (via Transmitter/BSSID field).

> ![Capture](/images/capture1.png)

Used the command “sudo aircrack-ng -w /usr/share/wordlists/rockyou.txt -b 00:14:6c:7e:40:80 /home/francis1/pictures/wpa.full.cap”. Where 00:14:6c:7e:40:80 is the MAC address/BSSID of the router/device.

> ![Capture](/images/progress1.png)

Aircrack-ng ran the brute-force attack using the provided dictionary. (in progress)

> ![Capture](/images/progress2.png)

Password was found: 444445555.

> ![Capture](/images/found.png)

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

Date: 25/05/2025
