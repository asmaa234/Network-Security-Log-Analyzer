# Network-Security-Log-Analyzer
A Python tool that parses network login logs, detects suspicious activity (failed login spikes), and identifies possible brute force attacks. Generates a timestamped security report.
What It Does
Reads a login log file line by line
Tracks failed login attempts per IP address
Tracks successful logins
Flags any IP that crosses a configurable failure threshold (default: 5)
Detects brute force attacks — IPs that failed repeatedly and then succeeded
Exports a timestamped `.txt` security report
Why I Built This
I work in IT/network support and wanted to understand how automated threat detection works at a fundamental level, beyond just using existing security tools. This project applies core security monitoring concepts (failed login tracking, brute force detection) using plain Python, with no external libraries required.
How It Works
Log parsing — each log line is split into date, time, IP, status, and username
Failed login tracking — a dictionary stores attempt counts, targeted usernames, and timestamps per IP
Threshold-based alerting — any IP with attempts ≥ threshold is flagged
Brute force detection — cross-checks flagged IPs against successful logins; if an IP failed repeatedly and later succeeded, it's flagged as a likely brute force attack
Report generation — results are printed to the console and saved as a timestamped `.txt` file
Example Log Format
```
2026-06-18 08:01:12 192.168.1.1 FAILED LOGIN user=admin
2026-06-18 08:01:30 192.168.1.1 SUCCESS LOGIN user=admin
```
Example Output
```
ALERT - Suspicious IP: 192.168.1.1
Failed attempts : 6
Targeted users  : admin
First attempt   : 2026-06-18 08:01:12
Last attempt    : 2026-06-18 08:01:25

CRITICAL - Brute force SUCCESS from: 192.168.1.1
6 failed attempts then logged in successfully
ACTION: Block this IP immediately
```
Tech Used
Python 3 (standard library only — `datetime`)
Google Colab / Jupyter Notebook
How to Run
Open `network_security_log_analyzer.ipynb` in Google Colab or Jupyter
Run all cells in order
A sample log is generated automatically (`sample_log.txt`) — or replace it with a real log file in the same format
View the printed report, and check the generated `security_report_<timestamp>.txt` file
Possible Future Improvements
Support real-world log formats (Apache, SSH auth logs, Windows Event Logs)
Add IP geolocation lookup for flagged addresses
Visualize attack patterns with charts
Add email/Slack alerting for real-time monitoring
Author
Asmaa
