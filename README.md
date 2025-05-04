# Network Scanner and Vulnerability Assessment Tool

A comprehensive network scanning and vulnerability assessment tool built in Python that helps identify security weaknesses in your network environment without requiring paid services or API keys.

## 🚀 Features

- **Automated Network Discovery**: Finds all devices on a local network using ARP scanning
- **Port Scanning**: Identifies open and closed ports on discovered devices
- **Service Detection**: Determines what services are running on open ports
- **Vulnerability Assessment**: Uses two methods to find security vulnerabilities:
  - Nmap NSE vulnerability scripts
  - Searchsploit (Exploit-DB) database queries
- **Firewall Detection**: Analyzes port scan results to determine firewall status
- **Report Generation**: Creates professional PDF reports of all findings
- **Data Persistence**: Stores all scan results in a SQLite database for historical analysis

## 📋 Requirements

- Python 3.6+
- Kali Linux (recommended) or any Linux distribution with:
  - Nmap
  - Searchsploit (from Exploit-DB)
- Python libraries:
  - scapy
  - netifaces
  - fpdf
  - subprocess
  - re
  - json
  - sqlite3

## 💻 Installation

1. Clone this repository:
```bash
git clone https://github.com/your-username/network-scanner.git
cd network-scanner
```

2. Install required Python libraries:
```bash
pip install scapy netifaces fpdf
```

3. Ensure you have Nmap and Searchsploit installed:
```bash
# For Debian/Ubuntu/Kali
sudo apt-get update
sudo apt-get install nmap exploitdb
```

## 🔧 Usage

1. Run the script with root/sudo privileges (required for network scanning):
```bash
sudo python3 network_scanner.py
```

2. Follow the interactive prompts:
   - Select a network interface
   - Choose port range to scan
   - Select vulnerability scanning method
   - Choose devices to scan

3. After scanning completes, you can generate a PDF report of the findings.

## 🖥️ Example Output

```
Network Scanner and Vulnerability Assessment Tool
--------------------------------------------------
Available network interfaces:
1. eth0 - 192.168.1.5
2. wlan0 - 10.0.0.15

Enter the network interface number (1-2): 1

Scanning network on eth0...

Found 12 devices:
1. IP: 192.168.1.1, MAC: a4:b1:e9:c3:22:11
2. IP: 192.168.1.5, MAC: 00:11:22:33:44:55
...

Enter port range to scan (default 1-1024): 1-100

Vulnerability scanning options:
1. Nmap vulnerability scripts (vuln)
2. Searchsploit (Exploit-DB)
3. Both

Choose vulnerability scanning method (1-3): 3

Scan all devices? (y/n): n
Enter device numbers to scan (comma-separated, e.g., 1,3,5): 1

Scanning device 1: IP 192.168.1.1, MAC a4:b1:e9:c3:22:11
  Scanning ports 1-100...
  Found 3 open ports and 97 closed ports
  Open ports: [22, 53, 80]
  Firewall status: Possibly firewalled
  Running Nmap vulnerability scan on 192.168.1.1 (ports: 22,53,80)...
  Found 2 potential vulnerabilities
  Results saved to database

Scanning complete.
Generate PDF report? (y/n): y
Report generated: network_scan_report.pdf
```

## 📊 Database Schema

The tool uses a SQLite database (`network_scan.db`) with the following schema:

```sql
CREATE TABLE devices (
    ip TEXT, 
    mac TEXT, 
    open_ports TEXT, 
    closed_ports TEXT, 
    vulnerabilities TEXT, 
    firewall_status TEXT
);
```

## 🛡️ Ethical Use

This tool is designed for security professionals, network administrators, and security researchers to assess networks they own or have explicit permission to test. Unauthorized scanning of networks is illegal in many jurisdictions and violates most acceptable use policies.

## 👥 Contributors

- Rishika Sinha
- Anshul Shukla
- Vikas
- Divyanshi
- Priyanshu

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🌟 Acknowledgments

- [Scapy](https://scapy.net/) for the powerful packet manipulation capabilities
- [Nmap](https://nmap.org/) for the robust port scanning and NSE scripts
- [Exploit-DB](https://www.exploit-db.com/) for the comprehensive vulnerability database
- Kali Linux for providing the security testing platform
