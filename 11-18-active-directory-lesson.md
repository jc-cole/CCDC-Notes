
# What are active directory domain services? 

- keeps track of many resources on a corporate network as objects

Some example active directory objects:
- User accounts
- Computer
- Groups
- File Shares
- Services

## What is an active directory domain?

- basically an identifier for a particular active directory

## How do objects work?

they represent resources within a network, such as user accounts, computers, and shared folders, and are organized in a hierarchical structure. Each object has attributes that define its properties

### User Objects 

- a user account allows access to network resources
- contains a username, password, group membership

### Computer Objects
represent individual computers within an organization's network and are defined by attributes such as computer name, operating system, and access permissions. 

### Group Objects
used to manage permissions and access control for users and computers.

There are two main types of groups: Security Groups, which can grant access to resources, and Distribution Groups, which are used for email distribution without security permissions

### Organizational Units
generic containers that you can use to group objects

### Group Policy Objects
collections of settings that administrators use to centrally manage Windows computers and user accounts in an Active Directory environment

## Domain Controller

For an active directory to exist, you need a domain controller

- Functions as a global catalog server, allows you to query domain objects 

## LDAP (Lightweight directory access protocol)

Protocol for authenticating and accessing directory services

Effectively how you find things in AD

You query by where things are.

Here is an example of an LDAP query that can be used to find Active Directory users with the User must change password at next logon option enabled:

```
Get-ADUser -LDAPFilter "(&(objectCategory=person)(objectClass=user)(pwdLastSet=0) \
(!(userAccountControl:1.2.840.113556.1.4.803:=2)))"
```

## NTLMyo

NTLM hashes are cryptographic representations of user passwords used in Active Directory for authentication. They are derived from the user's password using the MD4 hashing algorithm 

NTLM is buns and insecure!!! If you store passwords hashed using ntlm and they're exposed they can trivially be used to recover the passwords. 

## Kerberos 
is an authentication protocol used in Microsoft Active Directory to verify the identity of users and services on a network. 

## CCDC Specific Topics + Takeaways

### DISA STIG GPO 
- The DOD's official GPO (group policy object) for securing active directory

### Sysinternals Suite 
free collection of tools and troubleshooting utilities
- Process Monitor: enhanced task manager showing detailed process tress, handles, DLLs and parent-Child relations
- Process Explorer: realtime tool for monitoring filesystem
- Autoruns
- Sysmon

### VirusTotal

A free website for malaware/virus identification
- Matches uploaded file against a database of signatures

### A checklist for the competition:
- import DISA STIG GPOs
    - Do gpupdate -force
- Get sysinternals suite
- Powershell script to rotate every user's password
- Clean backdoors
- Remove tacticalRMM
- Disable guest users (no passwords)

### SUPER SECRET CHECKLIST!!!
- enable only one domain administrator
- delete all users except one domain administrator for yourself
