# SheidGuard-is-a-tool-that-has-the-potential-to-detect-Attacks-like-DoS-DDoS
ShieldGuard is a real-time DoS and DDoS detection tool built using Python, Scapy, and Flask. 
It captures live network traffic, analyzes packet behavior, identifies abnormal traffic spikes,
and classifies attack conditions. The system displays live status, traffic statistics, and attacker 
information through a web-based dashboard. Automatic mitigation is performed using firewall rules 
to block suspicious IPs. Includes PoC screenshots, attack simulation using hping3, and a clear 
technical stack.

Instructions for Running ShieldGuard
1. System Requirements

Kali Linux / Ubuntu (recommended)

Python 3.8+

sudo/root access

Internet connection

2. Install Required Packages
sudo apt update
sudo apt upgrade -y
sudo apt install python3 python3-pip python3-venv wireshark tcpdump hping3 -y

3. Create and Activate Virtual Environment
python3 -m venv shieldguard-env
source shieldguard-env/bin/activate

4. Install Python Dependencies

Install manually:

pip install scapy flask


OR using requirements file:

pip install -r requirements.txt

5. Set Up Project Folder
mkdir ShieldGuard
cd ShieldGuard


Create the main file:

nano shieldguard.py


Paste the complete ShieldGuard tool code into this file and save it.

6. Launch the ShieldGuard Tool
sudo python shieldguard.py


If the virtual environment is not active:

source shieldguard-env/bin/activate
sudo python shieldguard.py

7. Open the Web Dashboard

In a browser, visit:

http://127.0.0.1:5000


You should see:

Network status (Normal)

Packet count

Traffic spike graph

No attack detected yet

8. Simulate a DoS Attack (for testing)

Open a second terminal window:

sudo hping3 -S --flood -p 80 127.0.0.1


Expected dashboard changes:

Status switches to DDoS Attack

Graph turns red

Packet count spikes

Attacker IP displays

9. Stop the Attack

Press:

Ctrl + C


Dashboard should return to Normal state.

10. Stop ShieldGuard

In the main terminal running the tool:

Ctrl + C


This stops:

packet sniffing

detection engine

web dashboard

11. Exit Virtual Environment
deactivate

Important Notes
Localhost Blocking

Attacks from 127.0.0.1 are detected but NOT blocked.

This prevents blocking your own system during testing.

On real networks, external IPs will be auto-blocked via iptables.

Real Deployment

If using a real NIC instead of localhost:

Change this line in code:

INTERFACE = "lo"


To your actual interface:

INTERFACE = "eth0"


or

INTERFACE = "wlan0"
