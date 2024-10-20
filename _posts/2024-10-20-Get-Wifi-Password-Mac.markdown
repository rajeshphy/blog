---
layout: post
comments: true
title:  "How to Retrieve Wi-Fi Password Using macOS Terminal"
subtitle: "How to choose"
credits:
categories: [science, tech]
date:   2024-10-20 00:00:00 +0530
background: '/img/posts/bg-blog1.jpg'
---

# How to Retrieve Wi-Fi Password Using macOS Terminal

If you've connected to a Wi-Fi network previously and can't recall its password, macOS stores the credentials in the system's keychain. This guide will walk you through using the Terminal to retrieve the password for any saved network.

---

## Prerequisites
- **macOS**: These commands are designed for macOS users.
- **Administrator Access**: You'll need your system password to access the saved Wi-Fi credentials.
- **Terminal**: Open Terminal by searching for it in Spotlight (`Command + Space`) or through **Applications** > **Utilities** > **Terminal**.

---

## Steps to Retrieve the Wi-Fi Password

### 1. List Network Service Order
The first step is to identify the network services and their priorities on your Mac.

```bash
networksetup -listnetworkserviceorder
```

Explanation: This command lists all the network services available on your system, including Wi-Fi. Each network service is associated with a device identifier (like en0 for Wi-Fi). Look for the Wi-Fi service in the output, which will tell you its device identifier (usually en0).

2. Get the Current Wi-Fi Network

Next, check the name (SSID) of the Wi-Fi network your system is currently connected to using:

```bash
networksetup -getairportnetwork en0
```
Explanation: Replace en0 with the device identifier you found in the previous step if necessary. This command displays the name of the Wi-Fi network you are connected to.

3. List All Network Services

If you’re unsure which service is Wi-Fi, you can list all network services to confirm.

```bash
networksetup -listallnetworkservices
```
Explanation: This command provides a list of all network services configured on your Mac, allowing you to double-check the name of the Wi-Fi service (typically Wi-Fi or Wi-Fi 2).

4. Get Detailed Wi-Fi Information

For more detailed information about the Wi-Fi network you are connected to, use:

```bash
networksetup -getinfo Wi-Fi
```
Explanation: This will show information such as the IP address, router, and subnet mask of the Wi-Fi network. Although this doesn’t reveal the password, it helps you understand the connection details.

5. Retrieve the Wi-Fi Password

Now, use the following command to display the saved Wi-Fi password from macOS’s Keychain:

```bash
security find-generic-password -ga "SSID"
```
Explanation: Replace "SSID" with the actual name of the Wi-Fi network (e.g., “HomeWiFi”). After running the command, you’ll be prompted to enter your macOS user password. If the password is stored in the keychain, it will be displayed on the screen.

	•	The -ga flag ensures the password is displayed in plaintext.
	•	If the network is saved in Keychain, the system will prompt for administrator credentials and then show the password.

Example Walkthrough

Here’s an example of how this would work for a network called MyHomeWiFi:

	1.	First, list network services to confirm your Wi-Fi service:

```bash
networksetup -listnetworkserviceorder
```
Look for something like:

(1) Wi-Fi (Hardware Port: Wi-Fi, Device: en0)

	2.	Check the current Wi-Fi network:

```bash
networksetup -getairportnetwork en0
```
Output:

You are connected to: MyHomeWiFi

	3.	Now, retrieve the password using the SSID:

```bash
security find-generic-password -ga "MyHomeWiFi"
```
You’ll be prompted for your system password. After entering it, you’ll see:

password: "yourWiFiPassword"

Troubleshooting

	•	No Password Found: If the password is not found, it might not be saved in the Keychain. Double-check if the network name (SSID) is correct.
	•	Permission Issues: Ensure you have admin rights on your Mac. If not, you won’t be able to retrieve the password.
	•	Wi-Fi Not in List: If you don’t see Wi-Fi in the list, confirm that the device is connected and Wi-Fi is enabled.
