# Shell Considerations
- Always host listeners on common ports or mirror a port number used by the target.
- Always try nc, busybox nc and python for rev shells. PHP can be used but often fails.
- For powershell revshells, use nishangs shell. Gives a full shell
- For aspx, use Antak and use IEX + nishang to get a stable shell. MSFVenom stuff *can* work
- For php try all php shells. "Better ones" may fail where "worse ones" may work
  - Windows: WolfPHP, Ivan-Sineck
  - Linux: WolfPHP, Ivan-Sineck, PHP monkey

# URL Encoding
- When using exploits or LFIs, try unmodified path url, `../`, `+` encoding and `URL` encoding

# Enum / Outside abuse
- NMAP service detection for CVE
- Focus on unnatural ports, google them, if multiple google them together
- Dirbusting
  - Wordlists:
    - `Discovery/Web-Content/common.txt`
    - `directory-list-2-3-medium`
    - `/Discovery/Web-Content/raft-large-files.txt` and dir version
    - Service Related Wordlist 
    - `/backup`, `/dev`, `/<hostname>`
   
      
- Manual source code inspection for links / comments
- Breaking out of SSH "force SCP" wrappers by overwriting them or the authorized_keys file
- Check unknown services for specific enumeration techniques (ident for example)
- Hydra bruteforce against services
- Magical `cewl -d 5 -m 3`
- Password reuse for MYSQL,FTP,SSH
- Default Credentials
- admin:admin on any services
- admin:<empty>
- username:username
- username:<empty>
- Cred Reuse
- Null auth for 
  - FTP
  - SMB
  - RPC
  - LDAP
  - MySQL
  - PostgreSQL
- SQLi / SQLi Auth Bypass
- SMTP user enum
- SNMP with extended MIB snmpwalk
- SNMP community brute
- POP3 authenticated email retrieval
- Phish using links to HTTP or revshells.
- Postfix disclaimer file owned by root and writeable by us `https://viperone.gitbook.io/pentest-everything/writeups/pg-practice/linux/postfish`
- No sanitization on API endpoints / code evaluation. Put e.g. "user=2+2" into an API endpoint
# Post
## Windows
- Directories / Files to loot:
  - db.php
  - /inetpub
- Password reuse for *SQL,FTP,RDP
- username:username
- Cred Reuse

## Linux
- Files to loot:
  - db.php
  - wp-config.php
  - /var/www
- Dangerous SUID binary
  - Non-GTFO SUID binary
- SUID on writeable file ( echo >>)
- Bash History
- SSH Key "reuse"
- `mail` command
- Password reuse for *SQL,FTP,SSH,NFS
- username:username
- su username:username
- Cred Reuse
- cronjobs
- WildCard abuse (e.g. Tar wildcard abuse)
- writeable /etc/passwd
- Limited Shell escape via GTFO binary
- Group abuse
  - adm (use aureport if possible)
  - docker
  - disk
- Writeable .service file
- Write yourself into /etc/sudoers
- Highly probable kernel exploits
