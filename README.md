# Secure-Web-Server-Deployment-Using-Apache2-and-UFW
A practical guide to deploying a secure Apache2 web server on Ubuntu using UFW firewall configuration. Covers installation, firewall rules, service management, and security best practices for reliable web hosting.
# WebShield: Secure Web Server Deployment and IP-Based Access Control

A cybersecurity practical project demonstrating the deployment of an Apache2 web server on Kali Linux and the implementation of IP-based access control using UFW (Uncomplicated Firewall).

## Project Overview

WebShield focuses on deploying a web server and controlling which client devices can access it. Apache2 is used to host a custom webpage, while UFW firewall rules are configured to allow or block HTTP traffic based on the source IP address.

The project demonstrates how network-level access restrictions can help protect a web server from unauthorized client access.

## Objectives

- Install and configure Apache2 on Kali Linux.
- Deploy a custom cybersecurity webpage.
- Access the hosted webpage from different client devices.
- Configure UFW firewall rules for IP-based access control.
- Allow authorized devices to access the web server.
- Block an unauthorized device from accessing the server.
- Monitor and verify firewall activity through UFW logs.

## Tools and Technologies

| Tool | Purpose |

| Kali Linux | Web server operating system |
| Apache2 | Web server software |
| UFW | Firewall and access control |
| VirtualBox | Virtual machine environment |
| Windows 10 VM | Authorized client for testing |
| Firefox / Microsoft Edge | Browser-based access testing |
| Linux Terminal | Configuration and monitoring |

## Project Architecture

- **Server:** Kali Linux running Apache2.
- **Authorized client 1:** Windows virtual machine.
- **Authorized client 2:** Mobile device.
- **Restricted client:** Personal Windows laptop.

The server hosts a webpage over HTTP (TCP port 80). UFW rules are used to control access based on the source IP address.

## Implementation Steps

1. Install and verify Apache2 on Kali Linux.
2. Start the Apache2 service.
3. Create a custom webpage in `/var/www/html/index.html`.
4. Configure Apache2 access settings where required.
5. Install and enable UFW.
6. Set the default incoming policy to deny and outgoing policy to allow.
7. Create source-IP-based allow and deny rules for HTTP traffic.
8. Test access from authorized and restricted devices.
9. Monitor firewall events using system logs.

## Example Firewall Commands

**Set default policies:**

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

**Allow an authorized Windows VM:**

```bash
sudo ufw allow log from <WINDOWS_VM_IP> to any port 80 proto tcp
```

**Allow an authorized mobile device:**

```bash
sudo ufw allow log from <MOBILE_IP> to any port 80 proto tcp
```

**Block the restricted laptop:**

```bash
sudo ufw deny log from <LAPTOP_IP> to any port 80 proto tcp
```

**Enable and verify UFW:**

```bash
sudo ufw enable
sudo ufw status numbered
```

Replace the placeholders with the current IP addresses of your devices. IP addresses may change when DHCP assigns new addresses.

## Monitoring Firewall Logs

To monitor UFW events:

```bash
sudo journalctl -k -f | grep --line-buffered UFW
```

The logs can help verify whether traffic matched an allow or block rule.

- `[UFW ALLOW]` indicates traffic allowed by a firewall rule.
- `[UFW BLOCK]` indicates traffic blocked by a firewall rule.

## Expected Results

- Apache2 serves the custom webpage successfully.
- The authorized Windows VM can access the webpage.
- The authorized mobile device can access the webpage.
- The restricted Windows laptop is blocked from accessing the web server.
- UFW logs provide evidence of allowed and blocked traffic.

## Screenshots and Evidence

Project screenshots are available in the `screenshots/` directory.

Recommended evidence:

1. Apache2 service running in Kali Linux.
2. Custom webpage displayed in the browser.
3. Windows VM accessing the webpage.
4. Kali Linux localhost webpage.
5. Restricted laptop showing the connection failure.
6. UFW firewall rules.
7. UFW logs showing allowed and blocked traffic.

## Learning Outcomes

- Basic Linux server administration.
- Apache2 installation and configuration.
- Firewall configuration using UFW.
- IP-based network access control.
- HTTP traffic filtering.
- Firewall log monitoring and verification.
- Practical understanding of web server security.

## Future Enhancements

- Configure HTTPS using SSL/TLS.
- Add stronger Apache security settings.
- Implement intrusion detection and monitoring.
- Centralize firewall and web server logs.
- Add automated access testing.

## Project Screenshots

### Apache2 Web Server
![Apache2 Service](screenshots/01-apache-service-running.png)

### Custom Webpage
![Custom Webpage](screenshots/02-custom-webpage-kali.png)

### Authorized Windows VM
![Windows VM](screenshots/03-windows-vm-allowed.png)

### Restricted Laptop
![Blocked Laptop](screenshots/05-laptop-blocked.png)

### UFW Firewall Logs
![UFW Logs](screenshots/07-ufw-firewall-logs.png)

## Author

**Katila Raju**  
B.Tech – Information Technology  

This project was developed for educational and cybersecurity lab purposes. Test firewall configurations only on systems and networks that you own or are authorized to administer.
