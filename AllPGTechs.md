# Shell Considerations
- Always host listeners on common ports or mirror a port number used by the target.
- Always try nc, busybox nc and python for rev shells. PHP can be used but often fails.
- For powershell revshells, use nishangs shell. Gives a full shell
- For aspx, use Antak
- For php try all php shells. "Better ones" may fail where "worse ones" may work
  - Windows: WolfPHP, Ivan-Sineck
  - Linux: WolfPHP, Ivan-Sineck, PHP monkey


# Enum / Outside abuse
- NMAP for CVE
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
# Post
- Dangerous SUID binary
- Non-GTFO SUID binary
- SUID on writeable file ( echo >>)
- Password reuse for MYSQL,FTP,SSH
- username:username
- Cred Reuse
- writeable /etc/passwd
- Limited Shell escape via GTFO binary
- Group abuse
  - adm (use aureport if possible)
  - docker
  - disk
- Highly probable kernel exploits
