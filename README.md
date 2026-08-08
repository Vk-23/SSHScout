🔐 SSHScout - SSH Banner Grabber & CVE Checker

SSHScout is a lightweight and efficient Python tool for discovering SSH services, grabbing SSH banners, and checking detected OpenSSH versions against known vulnerabilities.

It is designed for network administrators, security researchers, penetration testers, and CTF players who need a fast way to identify SSH services across multiple IP addresses or domain names.

⚠️ For authorized security testing only. Only scan systems and networks that you own or have explicit permission to assess.

📜 Description

SSHScout helps quickly identify systems running SSH and collect useful information without requiring authentication.

The tool can:

Check whether TCP port 22 is accessible.
Retrieve SSH server banners.
Identify OpenSSH versions.
Check detected versions against known CVEs.
Scan multiple IP addresses and domains.
Perform concurrent scans using Python threading.
Provide a clear summary of vulnerable and non-vulnerable targets.

Whether you're performing a targeted security assessment or auditing a larger authorized network, SSHScout provides a quick overview of exposed SSH services.

🌟 Features
🔎 Port Check

Checks TCP port 22 and identifies:

Open SSH ports
Closed ports
Non-responsive hosts
📡 SSH Banner Retrieval

Retrieves the SSH identification banner without authentication.

Example:

SSH-2.0-OpenSSH_8.5p1-hpn15v2
🚨 Vulnerability Detection

Checks detected OpenSSH versions against known vulnerabilities, including:

CVE-2018-20685
CVE-2021-28041
CVE-2024-6387 (regreSSHion)
Other supported CVE/version mappings
⚡ Multi-threaded Scanning

Uses Python threading to scan multiple targets concurrently, significantly reducing scanning time compared with sequential checks.

📊 Detailed Results

Provides a concise summary containing:

Target IP/domain
SSH banner
Detected vulnerabilities
Scan status
🛠️ Requirements
Python 3.8+
Network access to the target
TCP port 22 accessible for banner detection

Check your Python version:

python3 --version
🚀 Installation

Clone the repository:

git clone https://github.com/MaulikxLakhani/SSHScout.git

Enter the project directory:

cd SSHScout

Run the tool:

python3 SSHScout.py

If the project provides a dependency file, install the dependencies with:

pip3 install -r requirements.txt
💻 Usage
Single IP Address
python3 SSHScout.py 192.168.1.1
Multiple IP Addresses
python3 SSHScout.py 192.168.1.1 192.168.1.2 192.168.1.3
Domain Names
python3 SSHScout.py example.com
IP Addresses and Domains
python3 SSHScout.py 91.191.200.30 proxy.domain.com
📋 Example Output

SSHScout provides a summary similar to:

+------------------+-----------------------------------------+-------------------------------+
|    Domain/IP     |               SSH Banner                |              CVE              |
+------------------+-----------------------------------------+-------------------------------+
| proxy.domain.com | SSH-2.0-OpenSSH_7.9p1 Debian-10+deb10u4 |        CVE-2018-20685         |
| 91.195.204.40    | SSH-2.0-OpenSSH_8.5p1-hpn15v2           | CVE-2021-28041, CVE-2024-6387 |
+------------------+-----------------------------------------+-------------------------------+

The final summary categorizes targets into:

🚨 Vulnerable
Servers running a detected vulnerable OpenSSH version.

🛡️ Not Vulnerable
Servers running a detected OpenSSH version that does not
match the supported vulnerable version ranges.

🔒 Closed Ports
Targets where TCP port 22 is closed or unavailable.
🔄 How It Works

SSHScout follows a simple scanning workflow:

             ┌─────────────────┐
             │  Target List    │
             │ IPs / Domains   │
             └────────┬────────┘
                      │
                      ▼
             ┌─────────────────┐
             │ Resolve Target  │
             └────────┬────────┘
                      │
                      ▼
             ┌─────────────────┐
             │ Check TCP :22   │
             └────────┬────────┘
                      │
             ┌────────┴────────┐
             │                 │
           Closed             Open
             │                 │
             ▼                 ▼
        🔒 Closed        📡 Grab Banner
                               │
                               ▼
                      ┌─────────────────┐
                      │ Detect Version  │
                      └────────┬────────┘
                               │
                               ▼
                      ┌─────────────────┐
                      │ CVE Comparison  │
                      └────────┬────────┘
                               │
                               ▼
                      🚨 / 🛡️ Result



 📚 References
    CVE-2024-6387 / regreSSHion
    Qualys research on the regreSSHion vulnerability
    Wiz blog on Detect and mitigate of CVE-2024-6387
    OpenSSH security advisories
    NVD vulnerability database