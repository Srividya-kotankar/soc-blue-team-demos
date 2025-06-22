# 🔐 Failed Login Alert Using Splunk

## 📌 Project Description

This project demonstrates how to detect multiple failed login attempts using Splunk. It simulates a brute-force attack scenario, triggers an alert based on custom SPL (Search Processing Language), and can be used as a basic SOC use-case.

## 🧰 Tools Used
- Splunk Enterprise / Free
- SPL (Search Processing Language)
- Sample Security Logs (Windows/Linux)

## 🚀 How It Works

1. Upload sample log data to Splunk.
2. Run the SPL query to identify:
   - Multiple failed logins from the same IP/User within 5 minutes.
3. Configure an alert action (e.g., email or pop-up alert).
4. Visualize results in Splunk dashboard.

## 🧪 Sample SPL Query

```spl
index=winlogbeat OR index=wineventlog sourcetype="WinEventLog:Security"
(EventCode=4625)
| stats count by user, host, src, _time
| where count >= 5
```

> 🔎 *This query checks for 5+ failed logins from same user/host.*

## 📂 Files Included

| File Name              | Description                          |
|------------------------|--------------------------------------|
| `failed_login_alert.spl` | SPL query for failed login alert     |
| `sample_logs.json`     | Sample log file for testing          |
| `screenshots/`         | Contains alert setup and result image|

## 📸 Screenshots

*(Add your screenshot in the `screenshots/` folder)*

## 🛡️ Use Case

This alert is useful for detecting brute-force login attempts, misconfigurations, or credential stuffing attacks.

## 🔧 How to Run

1. Import the `sample_logs.json` into your Splunk instance.
2. Copy and paste the `failed_login_alert.spl` into Splunk search.
3. Create an alert:
   - **Trigger condition**: if results > 0
   - **Trigger alert**: once per result or per time window
4. Done!

## 📚 References

- [Microsoft Event ID 4625](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4625)
- [Splunk Docs](https://docs.splunk.com)

## ✅ To-Do
- [ ] Add email alert trigger
- [ ] Add PowerShell script to generate logs
- [ ] Upload SIEM dashboard JSON (Optional)

## 🧠 Author

**Sri Vidya**  
Cybersecurity Enthusiast | ECE Grad | SOC Learner  
