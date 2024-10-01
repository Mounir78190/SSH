# SSH Protocol - Workshop Documentation

## Table of Contents

<span>1. Introduction</span> | <span>2. Steps and Commands Executed</span> | <span>3. Issues Faced and Solutions</span>  
<span>4. Theoretical Analysis</span> | <span>5. Conclusion</span> | <span>6. Resources</span>

## Introduction

This document provides a detailed overview of the SSH protocol exercises completed as part of the EECS 2024 program. The objective was to master secure remote connections via SSH, implement key-based authentication, transfer files, perform port forwarding, and secure the server against brute-force attacks using tools like Fail2Ban.

## Steps and Commands Executed

1.**SSH Connection**

- Command: `ssh mounir@192.67.197.121`
- Goal: Establish a secure connection to a remote server.

2.**Key-Based Authentication**

- Command to generate keys: `ssh-keygen -t ed25519`
- Command to copy the public key: `ssh-copy-id mounir@192.67.197.121`
- Goal: Ensure passwordless SSH login.

3.**Transferring Files with SCP and SFTP**

- SCP command: `scp file.txt mounir@192.67.197.121:/home/mounir/`
- SFTP: `sftp mounir@192.67.197.121`
- Goal: Transfer files securely between local and remote servers.

4.**Port Forwarding and Tunneling**

- Command: `ssh -L 8080:localhost:80 mounir@192.67.197.121`
- Goal: Redirect local port 8080 to a remote server's port 80, allowing secure web access.

5.**Securing SSH with Fail2Ban**

- Installation: `sudo apt install fail2ban`
- Configuration: Editing /etc/fail2ban/jail.local to activate SSH protection.
- Goal: Secure the SSH server by blocking IPs after multiple failed login attempts.

6.**Wireshark Installation**

- Installation: `sudo apt update && sudo apt install wireshark`
- startup: `sudo wireshark`
- Goal: Capture and analyze network traffic using Wireshark.

7.**Setting up Nginx**

- Installation: `sudo apt install nginx`
- startup: `sudo systemctl start nginx`
- Goal: Set up Nginx to handle web traffic, and redirect traffic from port 8080.


## Issues Faced and Solutions

Problem: Configuration issues when attempting to bind port 8080 for local port forwarding.
Solution: Utilized Nginx to bypass the conflict and correctly route traffic to the desired port. Nginx's reverse proxy capabilities allowed smoother management of port configurations and avoided conflicts with other services.

## Theoretical Analysis

SSH is essential for maintaining confidentiality and integrity when managing remote connections. The protocol encrypts all data exchanges, preventing third-party interception. Additional security measures like port change and Fail2Ban help protect against automated brute-force attacks, ensuring only authorized users can access the system.

   - Port Change: Moving away from the default port 22 helps reduce attacks from automated scripts.
   - Fail2Ban: Provides automated protection by banning IPs after repeated failed login attempts.

## Conclusion

Throughout this exercise, we gained hands-on experience in using SSH for secure communication, file transfer, and remote server management. By mastering key-based authentication, SCP/SFTP, and port forwarding, we reinforced our understanding of the protocol's security. Additionally, integrating Fail2Ban enhanced our server's resilience to external threats.

## Resources

1. ChatGPT for troubleshooting and explanations.
2. [Official SSH Documentation](https://man.openbsd.org/ssh)
3. [Fail2Ban Documentation](https://www.fail2ban.org/wiki/index.php/Main_Page)
4. [Wireshark Documentation](https://www.wireshark.org/docs/wsug_html_chunked/)
5. [Nginx Tutorial](https://www.nginx.com/resources/wiki/start/)
