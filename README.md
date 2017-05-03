# Project 10 - Honeypot

Time spent: **X** hours spent in total

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
