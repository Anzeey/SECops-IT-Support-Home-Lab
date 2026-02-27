# DAY 9 — Network Troubleshooting

**Objective:**  
To troubleshoot common network issues, including **DNS failure, DHCP IP conflicts, and internet connectivity issues**, using tools such as `nslookup`, `ping`, `tracert`, and `ipconfig`.

---

## 1. Simulate DNS Failure
- Configured client with an **incorrect DNS server** to simulate a DNS failure.  
- Verified using the `nslookup` command:

```cmd
nslookup google.com
Result: DNS resolution failed.

Screenshots:

Wrong_DNS_Config.png

nslookup_Failed.png

2. Fix DNS Configuration

Updated client with the correct DNS server (192.168.56.10).

Verified configuration using:

ipconfig /all


Tested DNS resolution again:

nslookup google.com


Result: DNS resolution successful.

Screenshots:

DNS_Fixed.png

nslookup_Success.png

3. Simulate DHCP IP Conflict

Assigned the same static IP (192.168.56.10) on a second VM to simulate IP conflict.

Verified the conflict using:

ipconfig /all


Result: Duplicate IP detected, connectivity issues observed.

4. Release and Renew IP Configuration

Resolved IP conflict by releasing and renewing IP:

ipconfig /release
ipconfig /renew
ipconfig /all


Result: New unique IP assigned, conflict resolved.

5. Simulate No Internet Access

Configured a wrong default gateway to simulate no internet:

netsh interface ip set address "Ethernet" static <IP> <Subnet> <Wrong_Gateway>


Verified connectivity using:

ping <Gateway_IP>
ping 8.8.8.8
ping google.com
tracert google.com
ipconfig /all


Result: Unable to reach internet; diagnostic commands helped identify the issue.

Conclusion

Successfully identified and resolved DNS issues, IP conflicts, and connectivity failures.

Used systematic troubleshooting with nslookup, ping, tracert, and ipconfig.

Documented results and screenshots for portfolio presentation.