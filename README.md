# Hermes Security Analyzer

**A Comprehensive Remote System Security Analysis Platform**

<div align="center">
  <img src="./images/hermes1.png" width="30%" alt="Dashboard"/>
  <img src="./images/hermes2.png" width="30%" alt="Security Analysis"/>
  <img src="./images/hermes3.png" width="30%" alt="Process Monitoring"/>
  <br/>
  <img src="./images/hermes4.png" width="30%" alt="Network Analysis"/>
  <img src="./images/hermes5.png" width="30%" alt="Log Management"/>
  <img src="./images/hermes6.png" width="30%" alt="Service Analysis"/>
  <br/>
  <img src="./images/hermes7.png" width="30%" alt="Hardening Checks"/>
  <img src="./images/hermes8.png" width="30%" alt="Kernel Analysis"/>
  <img src="./images/hermes9.png" width="30%" alt="Reports"/>
</div>

## 🚀 Overview

**Hermes Security Analyzer** is a powerful Flask-based web application designed for comprehensive remote Linux system security analysis. It performs deep security assessments without making any modifications to the target systems, making it ideal for security audits, incident response, and compliance assessments.

### Key Features
- **Read-Only Analysis**: Performs deep security analysis without changing the target system
- **Comprehensive Scanning**: 8 different security analysis modules
- **Detailed Reports**: Professional HTML reports with visual analytics
- **Cross-Platform**: Works from both Linux and Windows environments
- **No Agent Required**: Uses SSH for remote analysis

## ✨ Features

### Core Analysis Capabilities

| Feature | Description |
|---------|-------------|
| 🔍 **Vulnerability Scanning** | CVE detection using NVD database with CVSS scoring |
| 🌐 **Port Analysis** | Comprehensive port scanning with risk scoring and threat classification |
| ⚙️ **Service Analysis** | Deep inspection of system services with IOC matching |
| 🧩 **Process Analysis** | Real-time process monitoring with anomaly detection |
| 🧠 **Kernel Module Analysis** | Rootkit detection and module integrity verification |
| 📦 **Software Audit** | Package analysis with threat intelligence matching |
| 👤 **User Analysis** | Privilege audit and suspicious account detection |
| 🛡️ **Hardening Checks** | Comprehensive security posture assessment |

### Advanced Capabilities

- **Threat Intelligence**: Real-time matching against known malware patterns
- **Risk Scoring**: Automated risk assessment for ports and services
- **Resource Monitoring**: CPU and memory abuse detection
- **Report Generation**: Professional HTML and JSON reports
- **Export Options**: Export reports in multiple formats

## 🛠️ Technical Architecture

### Built With
- **Flask**: Web framework with modern UI design
- **Paramiko**: SSH connectivity with connection pooling
- **Threading**: Concurrent analysis for performance
- **Modern UI**: Clean, responsive interface

### Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    Hermes Security Analyzer                  │
├─────────────────────────────────────────────────────────────┤
│  Web Interface (Flask + Modern Design)                      │
│  ├── Dashboard                                              │
│  ├── Report Viewer                                          │
│  ├── Report Manager                                         │
│  └── Export Functions                                       │
├─────────────────────────────────────────────────────────────┤
│  Analysis Engine                                            │
│  ├── CVE Scanner (NVD Integration)                          │
│  ├── Port Scanner (ss/ netstat)                             │
│  ├── Service Analyzer (systemctl)                           │
│  ├── Process Analyzer (ps)                                  │
│  ├── Kernel Module Analyzer (lsmod/modinfo)                 │
│  ├── Package Auditor (dpkg/rpm/pacman)                     │
│  ├── User Auditor (getent/passwd)                           │
│  └── Hardening Checker                                      │
├─────────────────────────────────────────────────────────────┤
│  SSH Connection Manager                                     │
│  ├── Connection Pooling                                     │
│  ├── Keep-alive Management                                  │
│  └── Retry Logic                                            │
└─────────────────────────────────────────────────────────────┘
```

## 📋 Prerequisites

### Local Machine (Where Hermes runs)
- **Python 3.9+** (Python 3.10, 3.11, 3.12 recommended)
- Modern web browser
- 4GB+ RAM (8GB recommended)
- Internet connection (for CVE database updates)
- **Debian/Ubuntu Linux** (for .deb installation)

### Target Linux Servers (Being analyzed)
- SSH server (port 22 or custom)
- sudo privileges for SSH user (for some checks)
- Linux (Ubuntu/Debian/CentOS/RHEL recommended)

## 🔧 Installation

### Option 1: Install via .deb Package (Recommended for Debian/Ubuntu)

#### Download and Install
```bash
# Download the .deb package
wget https://github.com/KooshaYeganeh/Hermes/releases/latest/download/hermes_1.0.0_all.deb

# Install the package
sudo dpkg -i hermes_1.0.0_all.deb

# Fix any dependency issues
sudo apt-get install -f
```

#### Build from Source
```bash
# Clone the repository
git clone https://github.com/KooshaYeganeh/Hermes.git
cd Hermes

# Build the .deb package
chmod +x build_deb.sh
./build_deb.sh

# Install
sudo dpkg -i hermes_1.0.0_all.deb
sudo apt-get install -f
```

### Option 2: Manual Installation (Development)

```bash
# Clone the repository
git clone https://github.com/KooshaYeganeh/Hermes.git
cd Hermes

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the application
python app/main.py
```

## 📦 Package Installation Details

When installed via .deb package, Hermes is organized as follows:

| Location | Purpose |
|----------|---------|
| `/usr/share/hermes/` | Application files |
| `/usr/share/hermes/app/` | Main application code |
| `/etc/hermes/settings.py` | Configuration file |
| `/var/log/hermes/` | Log files (access.log, error.log) |
| `/var/lib/hermes/reports/` | Generated security reports |
| `/var/lib/hermes/uploads/` | Temporary uploads |
| `/usr/bin/hermes` | Launcher script |
| `/etc/systemd/system/hermes.service` | Systemd service file |

## 🚀 Usage

### After .deb Installation

#### 1. Configure SSH Credentials
```bash
# Edit the configuration file
sudo nano /etc/hermes/settings.py
```

Update these values:
```python
SSH_HOST = "192.168.1.100"  # Your target server IP
SSH_USERNAME = "your_username"
SSH_PASSWORD = "your_password"  # Or use SSH_KEY
```

#### 2. Start Hermes

**Option A: Using systemd service (Recommended)**
```bash
# Start the service
sudo systemctl start hermes

# Enable to start on boot
sudo systemctl enable hermes

# Check status
sudo systemctl status hermes

# View logs
sudo journalctl -u hermes -f
```

**Option B: Using the launcher**
```bash
# Run directly
hermes
```

**Option C: Manual run**
```bash
cd /usr/share/hermes
source venv/bin/activate
python app/main.py
```

#### 3. Access the Web Interface
Open your browser and navigate to:
```
http://localhost:5050
```

**Default Credentials**:
- Username: `admin`
- Password: `admin`
- ⚠️ **CHANGE THESE IMMEDIATELY!**

### Development Usage (Manual Install)

```bash
# Activate virtual environment
source venv/bin/activate

# Run the application
python app/main.py

# Or with custom settings
export FLASK_APP=app/main.py
export FLASK_ENV=development
python -m flask run --host=0.0.0.0 --port=5050
```

## 📊 Usage Guide

### 1. Dashboard
The dashboard provides a comprehensive overview of your security posture:
- System information (hostname, OS, kernel, uptime)
- Security service status
- Quick actions for scanning and reporting

### 2. Running a Security Scan
1. Click **"Initialize Comprehensive Scan"**
2. Wait for the scan to complete (typically 30-60 seconds)
3. View the detailed report with all findings

### 3. Understanding the Report
The report is organized into logical sections:
- **System Information**: Hardware and OS details
- **Executive Summary**: High-level security overview
- **CVEs Found**: Vulnerabilities with severity scoring
- **Suspicious Ports**: Open ports with risk assessment
- **Suspicious Services**: Services with IOC matches
- **Suspicious Processes**: Processes with anomaly detection
- **Suspicious Kernel Modules**: Module integrity issues
- **Suspicious Packages**: Software with threat matches
- **Suspicious Users**: Privilege and account anomalies
- **Hardening Status**: Security configuration review

### 4. Exporting Reports
- **HTML Report**: Viewable in any browser
- **JSON Export**: For integration with other tools
- **Text Export**: Plain text format for documentation

## 🔧 Configuration

### Main Configuration File
Location: `/etc/hermes/settings.py`

```python
# SSH Configuration
SSH_HOST = "192.168.1.100"      # Target server IP
SSH_PORT = 22
SSH_USERNAME = "your_username"
SSH_PASSWORD = "your_password"  # Or use SSH_KEY
SSH_KEY = None                  # Path to private key file

# Session Configuration
SESSION_TYPE = 'filesystem'
SESSION_PERMANENT = False
PERMANENT_SESSION_LIFETIME = 3600

# Paths
LOG_DIR = '/var/log/hermes'
REPORT_DIR = os.path.join(LOG_DIR, 'reports')

# Cache Settings
CACHE_TTL = 300
CACHE_MAX_SIZE = 100

# Security Settings
SECRET_KEY = 'change-this-secret-key-in-production'
PASSWORD_HASH = 'bcrypt'

# Flask Settings
HOST = '0.0.0.0'
PORT = 5050
DEBUG = False
```

## 🔒 Security Considerations

### Best Practices
1. **Authentication**: Change default credentials immediately after installation
2. **Network Security**: Restrict access using firewalls (e.g., `ufw allow from 192.168.1.0/24 to 5050`)
3. **SSH Security**: Use key-based authentication for target systems
4. **Regular Updates**: Keep dependencies updated
5. **Log Monitoring**: Regularly review application logs
6. **HTTPS**: Use a reverse proxy (nginx) with SSL in production

### Security Features
- Session-based authentication
- Password hashing with bcrypt
- Role-based access control
- Secure session management
- Read-only analysis (no system modifications)

## 🧪 Testing & Validation

### Tested Environments
- Ubuntu 20.04/22.04/24.04 LTS
- Debian 11/12
- CentOS 7/8
- RHEL 8/9
- Windows 10/11 (client only)

### Performance Metrics
- Scan time: 30-60 seconds (average system)
- Memory usage: ~200MB
- CPU usage: Minimal (analysis is remote)
- Concurrent connections: Up to 10 hosts

## 📋 Systemd Service Management

```bash
# Start Hermes service
sudo systemctl start hermes

# Stop Hermes service
sudo systemctl stop hermes

# Restart Hermes service
sudo systemctl restart hermes

# Check status
sudo systemctl status hermes

# Enable at boot
sudo systemctl enable hermes

# Disable at boot
sudo systemctl disable hermes

# View logs
sudo journalctl -u hermes -f
```

## 🗑️ Uninstallation

### Complete Removal
```bash
# Download the removal script
wget https://raw.githubusercontent.com/KooshaYeganeh/Hermes/main/remove_hermes.sh

# Make it executable
chmod +x remove_hermes.sh

# Run it (will prompt for confirmation)
sudo ./remove_hermes.sh
```

### Quick Removal
```bash
# Remove without prompts
sudo dpkg --purge hermes
sudo rm -rf /usr/share/hermes /var/log/hermes /var/lib/hermes /etc/hermes
sudo rm -f /usr/bin/hermes /etc/systemd/system/hermes.service
sudo systemctl daemon-reload
```

## 🐛 Troubleshooting

### Common Issues

#### 1. Python version issues
```bash
# Check Python version
python3 --version

# Install Python 3.9+ on Ubuntu
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.9 python3.9-venv python3.9-dev
```

#### 2. Service fails to start
```bash
# Check logs
sudo journalctl -u hermes -n 50
sudo tail -f /var/log/hermes/error.log

# Verify configuration
sudo python3 -c "import settings; print('Config OK')"
```

#### 3. SSH Connection issues
```bash
# Test SSH manually
ssh -v username@target_host

# Check SSH key permissions
chmod 600 ~/.ssh/id_rsa
```

#### 4. Port already in use
```bash
# Change port in /etc/hermes/settings.py
sudo nano /etc/hermes/settings.py
# Set PORT = 5051 or another available port
```

#### 5. Permission issues
```bash
# Fix permissions
sudo chown -R root:root /usr/share/hermes
sudo chmod 755 /usr/share/hermes
sudo chmod 755 /var/log/hermes
sudo chmod 755 /var/lib/hermes
```

## 📝 Contributing

We welcome contributions! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### Coding Standards
- Follow PEP 8 for Python code
- Include docstrings for all functions
- Add tests for new features
- Update documentation

## 📄 License

GPL-3.0 License - See [LICENSE](LICENSE) for details

## 👥 Team

- **KYGnus**
- Contributions welcome!

## 📞 Support

- **GitHub Issues**: [Report a bug](https://github.com/KooshaYeganeh/Hermes/issues)
- **Email**: kygnus.co@proton.me
- **Telegram**: [@KYGnus](https://t.me/KYGnus)

---

<div align="center">
  <p>Built with ❤️ for the security community</p>
  <p>
    <a href="https://kygnus.github.io">Website</a> ·
    <a href="mailto:kygnus.co@proton.me">Email</a> ·
    <a href="https://t.me/KYGnus">Telegram</a> ·
    <a href="https://github.com/KooshaYeganeh/Hermes">GitHub</a>
  </p>
</div>
