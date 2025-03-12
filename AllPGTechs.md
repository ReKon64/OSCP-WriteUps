# Shell Considerations
- Always host listeners on common ports or mirror a port number used by the target.
- Always try nc, busybox nc and python for rev shells. PHP can be used but often fails.
- For powershell revshells, use nishangs shell. Gives a full shell
- For aspx, use Antak
- For php try all php shells. "Better ones" may fail where "worse ones" may work
  - Windows: WolfPHP, Ivan-Sineck
  - Linux: WolfPHP, Ivan-Sineck, PHP monkey


# Enum / Outside abuse
- NMAP service detection for CVE
- Focus on unnatural ports, google them, if multiple google them together
- Dirbusting
- `http://$ip/<target hostname>`
- Breaking out of SSH "force SCP" wrappers by overwriting them or the authorized_keys file
- Check unknown services for specific enumeration techniques (ident for example)
- Hydra bruteforce against services
- `Magical` cewl -d 5 -m 3
- Password reuse for MYSQL,FTP,SSH
- Default Credentials
- admin:admin on ANY services
- username:username
- Cred Reuse
- Null auth for 
  - FTP
  - SMB
  - RPC
  - LDAP
  - MySQL
  - PostgreSQL
- SMTP user enum
- SNMP with extended MIB snmpwalk
- SNMP community brute
- POP3 authenticated email retrieval
- Phish using links to HTTP or revshells.
- Postfix disclaimer file owned by root and writeable by us `https://viperone.gitbook.io/pentest-everything/writeups/pg-practice/linux/postfish`
- No sanitization on API endpoints / code evaluation. Put e.g. "user=2+2" into an API endpoint
# Post
## Windows
- Files to loot:
  - db.php
  - inetpub
- Password reuse for *SQL,FTP,RDP
- username:username
- Cred Reuse

## Linux
- Files to loot:
  - db.php
  - wp-config.php
- Dangerous SUID binary
- Non-GTFO SUID binary
- SUID on writeable file ( echo >>)
- Password reuse for *SQL,FTP,SSH,NFS
- username:username
- su username:username
- Cred Reuse
- writeable /etc/passwd
- Limited Shell escape via GTFO binary
- Group abuse
  - adm (use aureport if possible)
  - docker
  - disk
- Writeable .service file
- Write yourself into /etc/sudoers
- Highly probable kernel exploits
