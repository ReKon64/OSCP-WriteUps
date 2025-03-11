# ClamAV
## Chain
Hostname + milter(nmap) -> CVE RCE (AS ROOT)
## Summary
`sudo nmap 192.168.142.42 -Pn -p- -sS -sV`

Realize milter is listed on scan.

Realize ClamAV is hostname.

`searchsploit clamav milter`
https://www.exploit-db.com/exploits/4761

The script will open up port 31337 to receive connections on.

nc 192.168.142.42 31337

Get root
