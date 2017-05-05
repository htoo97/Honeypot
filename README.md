# Project 10 - Honeypot

Time spent: **7** hours spent in total

> Objective: Setup a honeypot and provide a working demonstration of its features.

### Required: Overview & Setup

- [x] A basic writeup (250-500 words) on the `README.md` desribing the overall approach, resources/tools used, findings
- [x] A specific, reproducible honeypot setup, ideally automated. There are several possibilities for this:
	- A Vagrantfile or Dockerfile which provisions the honeypot as a VM or container
	- A bash script that installs and configures the honeypot for a specific OS
	- Alternatively, **detailed** notes added to the `README.md` regarding the setup, requirements, features, etc.
	
* **Setup**: The honeypot was set up following Modern Honey Network's multi-snort honeypot sensor management, using a network of VMs set up using Vagrant and VirtualBox, small footprint snort installations, stealthy dinoaeas and a centralized server management site.
* **Intrusion Detection Software**: Snort, Kippo, Conpot, and Dionaea.
* **Management Server**: Flask application that exposes an HTTP API that honeypots can use to:
  * Download a deploy script
  * Connect and register
  * Download snort rules 
  * Send intrusion detection logs
* It also allows systems administrators to:
  * View a list of new attacks
  * Manage snort rules: enable, disable, download
* **Installation**: 
  * Install Git
   ```# on Debian or Ubuntu
      $ sudo apt-get install git -y
    
      # on Centos or RHEL
      $ sudo yum install -y git
   ```
  * Install MHN
   ```$ cd /opt/
      $ sudo git clone https://github.com/threatstream/mhn.git
      $ cd mhn/
      $ sudo ./install.sh
   ```
  * After installation, a number of services should be running. To check:
   ```
      $ sudo supervisorctl status 
   ```
  * **Deploying honeypots with MHN**:
    1. Login to your MHN server web app.
    2. Click the "Deploy" link in the upper left hand corner.
    3. Select a type of honeypot from the drop down menu (e.g. "Ubuntu 12.04 Dionaea").
    4. Copy the deployment command.
    5. Login to a honeypot server and run this command as root.
  * **Integration with Splunk and ArcSight**: Splunk will log the events as key/value pairs to /var/log/mhn-splunk.log. This log should be monitored by the SplunkUniveralForwarder. Arcsight will log the events as CEF to /var/log/mhn-arcsight.log
   ```$ cd /opt/mhn/scripts
      $ sudo ./install_hpfeeds-logger-splunk.sh
      $ sudo ./install_hpfeeds-logger-arcsight.sh
   ```

### Required: Demonstration

- [x] A basic writeup of the attack (what offensive tools were used, what specifically was detected by the honeypot)
- [x] An example of the data captured by the honeypot (example: IDS logs including IP, request paths, alerts triggered)
- [x] A screen-cap of the attack being conducted
    
### Optional: Features
- Honeypot
	- [ ] HTTPS enabled (self-signed SSL cert)
	- [ ] A web application with both authenticated and unauthenticated footprint
	- [x] Database back-end
	- [ ] Custom exploits (example: intentionally added SQLI vulnerabilities)
	- [ ] Custom traps (example: modified version of known vulnerability to prevent full exploitation)
	- [ ] Custom IDS alert (example: email sent when footprinting detected)
	- [ ] Custom incident response (example: IDS alert triggers added firewall rule to block an IP)
- Demonstration
	- [ ] Additional attack demos/writeups
	- [ ] Captured malicious payload
	- [ ] Enhanced logging of exploit post-exploit activity (example: attacker-initiated commands captured and logged)
<img src='http://i.imgur.com/GTHl2Bu.gif' title='Nmap Demo' width='' alt='Nmap demo' />

## LICENSE

Modern Honeypot Network

Copyright (C) 2017 - Anomali, Inc.

This program free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA
