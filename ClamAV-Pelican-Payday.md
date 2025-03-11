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

- NOPASSWD on `gcore`, can be used to dump memory

- Use `gcore` to dump custom "password-store" process

- `strings` the output to find credentials in output file and use them to `su` as root

## Summary
`sudo nmap 192.168.189.98 -sS -sV -p-`

`8080,8081,44091` Probaby connected with each other and Zookeeper

Visit `8080` to see Exhibitor for Zookeper interface

Realize you can put scripts in there. Searchsploit for a proven exploit `https://www.exploit-db.com/exploits/48654`

Receive shell as `charles`. Run linpeas and figure out that you have NOPASSWD on `gcore`

Read up on it online, can dump process data.

Check for processes that can be dumped for creds.

Realize there's conveniantly a password-store process running. Dump it with `sudo -u root /usr/bin/gcore -a -o <outputfile> <pid>`

Run strings on dump. Find password. `su` to root using that password.

#Payday
## Chain
- Nmap -> CS Cart on 80
- Check `admin:admin`
- Search for CVE. You can get RCE as patrick or try LFI
- LFI -> `/etc/passwd`
- Check ssh for `patrick:patrick`
- `sudo -l` -> `sudo su`
