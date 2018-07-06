---
### LDAP Search with Kerberos!

---
### This command is pretty straight forward:
----
```bash
ldapsearch -Q -Y GSSAPI -h adServer01.macbytes.io -b "DC=macbytes,DC=io" "(sAMAccountName=edward.shorrock)" | grep 'siteCode'
```
---
### We can even let Jamf Pro fill in variables
```bash
#
# SET VARIABLES FROM JAMF PRO
#
ldapServer=${4}
rootDN=${5}
searchFilterAttribute=${6}
searchAccount=${7}
targetAttribute=${8}

#
# POPULATE NEEDED VALUES FOR LAUNCHCTL
#
loggedInUserPid=$(python -c 'from SystemConfiguration import SCDynamicStoreCopyConsoleUser; username = SCDynamicStoreCopyConsoleUser(None, None, None)[1]; print(username);')
launchctlCmd=$(python -c 'import platform; from distutils.version import StrictVersion as SV; print("asuser") if SV(platform.mac_ver()[0]) >= SV("10.10") else "bsexec"')

result=$(launchctl "$launchctlCmd" "$loggedInUserPid" ldapsearch -Q -Y GSSAPI -h "${ldapServer}" -b "${rootDN}" "(${searchFilterAttribute}=${searchAccount})" | grep "${targetAttribute}")
result=$(echo ${result} | cut -d " " -f 2)
```


