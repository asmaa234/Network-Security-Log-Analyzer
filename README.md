# Network-Security-Log-Analyzer
A Python tool that parses network login logs, detects suspicious activity (failed login spikes), and identifies possible brute force attacks. Generates a timestamped security report.

What It Does
Tracks failed and successful login attempts per IP
Flags IPs that cross a failure threshold (default: 5)
Detects brute force attacks (repeated failures followed by a success)
Exports a timestamped `.txt` report
Example Output
```
ALERT - Suspicious IP: 192.168.1.1
Failed attempts : 6
Targeted users  : admin

CRITICAL - Brute force SUCCESS from: 192.168.1.1
6 failed attempts then logged in successfully
ACTION: Block this IP immediately
```
How to Run
Open `network_security_log_analyzer.ipynb` in Google Colab or Jupyter
Run all cells in order
A sample log (`sample_log.txt`) is included for testing
Tech
Python 3 — standard library only.
Author
Asmaa Maree— focused on cybersecurity and AI.
