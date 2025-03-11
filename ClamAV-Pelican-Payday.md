# ClamAV
## Chain
- Hostname + nmap -> milter service

- searchsploit ClamAV + milter for CVE RCE (AS ROOT)
## Summary
`sudo nmap 192.168.142.42 -Pn -p- -sS -sV`

Realize milter is listed on scan.

Realize ClamAV is hostname.

`searchsploit clamav milter`
https://www.exploit-db.com/exploits/4761

The script will open up port 31337 to receive connections on.

`nc 192.168.142.42 31337` Gets you shell as root.

# Pelican
## Chain
- nmap -> Exhibitor for ZooKeeper

- searchsploit for Exhibitor for CVE RCE (AS USER)

- NOPASSWD on gcore, can be used to dump memory

- Use gcore to dump custom "password-store" process

- `strings` the output to find credentials in output file and use them to `su` as root
