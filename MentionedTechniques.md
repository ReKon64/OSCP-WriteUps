# Shell Troubleshooting
- Always host listeners on common ports or mirror a port number used by the target.
- Always try nc, busybox nc and python for rev shells. PHP can be used but often fails.
- For powershell revshells, use nishangs shell. Gives a full shell
- For aspx, use Antak and use IEX + nishang to get a stable shell. MSFVenom stuff *can* work
- For php try all php shells. "Better ones" may fail where "worse ones" may work
  - Windows: WolfPHP, Ivan-Sineck
  - Linux: WolfPHP, Ivan-Sineck, PHP monkey
- If your shell behaves strangely, try starting another one from it.

# URL Encoding
- When using exploits or LFIs, try unmodified path url, `../`, `+` encoding and `URL` encoding

# SMB Tips
- Use `mput` and `mget`. Sometimes these commands can do "expected" behaviour that `put` and `get` don't.
- Avoid losing time by first putting `ntlm_theft.py` payloads that coerce SMB connections before constructing phishing files with shells.
- Do all nmap SMB scripts against windows hosts.

# FTP
- anon and user:user
- One port may host multiple folders that can be exposed under different credentials
- Linux common root: /var/ftp/pub
- Windows common root: (?) C:\ftp

# LFI Tips
- Google vulnerable software's docs and or github. Check 'set-up' guides and 'password recovery / change' guides.
- Any files worth looting in POST are viable loot here too.
- Check wrappers. They are in scope.

# Proprietary Software
- Decryption exploits
- Easy to exploit LFIs due to abundance of information about config file locations

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
- WhatWeb medium aggressive
- phpinfo.php for directive info
- Also check phpinfo.php for additional technology that might be vulnerable (e.g. SPX)
- PHP wrappers for LFI
- Looting Java files for SQL queries
- Vulnerable file upload
  - Magic Number manipulation (remember to check how the file looks after the edit)
  - Extension bypasses
  - File Type header manipulation
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
- admin:password
- Cred Reuse
- Null auth for 
  - FTP
  - SMB
  - RPC
  - LDAP
  - MySQL
  - PostgreSQL
- SQLi / SQLi Auth Bypass
- SSRF, like putting your SMB share into a field to coerce authentication
- Abusing setup phase software. Read docs... lots of docs. Read githubs...
  - Rouge MySQL server https://github.com/allyshka/Rogue-MySql-Server/blob/master/roguemysql.php
- VHOST bruteforce / enumeration
  - Remember to loot files for vhosts too.
- Exposed `.git` (don't care about forbidden. `git-dump`er it anyways)
- Thorough wpscan
  - Exposed `wp-uploads`
  - Installed vulnerable Core or plugins
- SMTP user enum
- SNMP with extended MIB snmpwalk
- SNMP community brute
- POP3 authenticated email retrieval
- Phish using links to HTTP or revshells.
- Postfix disclaimer file owned by root and writeable by us `https://viperone.gitbook.io/pentest-everything/writeups/pg-practice/linux/postfish`
- No sanitization on API endpoints / code evaluation. Put e.g. "user=2+2" into an API endpoint
- Redis exploitation and modifying relevant exploits
- /proc files may include credentials... `I hate that jenkins exploit alright?`
# Post
## Windows
- Directories / Files to loot:
  - db.php
  - /inetpub
- Password reuse for *SQL,FTP,RDP
- username:username
- Cred Reuse
- Service hidden behind FW / Service on 127.0.0.1
- Always Install elevated
- Creds in Running service (itm4n PrivEscCheck for this)
- Overwrite a service.exe file
- systeminfo + wesng.py

## Linux
- PWNKit https://github.com/ly4k/PwnKit
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
- admin:password
- su username:username
- Cred Reuse
- cronjobs
  - WildCard abuse (e.g. Tar wildcard abuse, 7zip @ abuse)
  - Use pspy to spy on stuff linpeas won't catch. They really love those.
- Service hidden behind FW / Service on 127.0.0.1
- Limited Shell escape via GTFO binary
- Group abuse
  - adm (use aureport if possible)
  - docker
  - disk
- Writeable .service file
- Shared Object hijacking
- `git show`
- Local git repo that's updateable by us and files will be executed automatically.
- Write yourself into /etc/sudoers
- Writeable /etc/passwd
- Highly probable kernel exploits

# Box Types
CVE -> Privesc -> Root
Weak Creds -> Abuse Builtin functionality -> Privesc -> Root

