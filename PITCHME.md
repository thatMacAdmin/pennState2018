---?color=#74992e
### Configuration for AD LDS
#### Code Examples

----
### Tell AD LDS About your Source AD:

```xml
<description>MacBytes User Sync</description>
<security-mode>object</security-mode>
<source-ad-name>macbytes.io</source-ad-name>
<source-ad-partition>dc=macbytes,dc=io</source-ad-partition>
<source-ad-account>thatmacadmin</source-ad-account>
<account-domain>macbytes</account-domain>
<target-dn>dc=jss,dc=macbytes,dc=io</target-dn>
```

---
### Tell ADAM What to Sync:

```xml
<base-dn>ou=Users,ou=Users and Groups,dc=macbytes,dc=io</base-dn>
<base-dn>ou=Application Groups,ou=Users and Groups,dc=macbytes,dc=io</base-dn>
<base-dn>ou=App Grps,ou=Unix,dc=macbytes,dc=io</base-dn>
```

---
### Set Object Filter:

```xml
<object-filter>(&#124;(objectCategory=Person)(objectCategory=OrganizationalUnit)(objectCategory=Group))</object-filter>
```

---
### Configure Sync Attributes
```xml
<attributes>
    <include>userPrincipalName</include>
    <include>title</include>
    <include>sAMAccountName</include>
    <include>uid</include>
    <include>cn</include>
    <include>sn</include>
    <include>streetAddress</include>
    <include>telephoneNumber</include>
    <include>givenName</include>
    <include>member</include>
    <exclude></exclude>
</attributes>
```

---
### Get User-Object-Proxy Working:

```xml
<user-proxy>
    <source-object-class>user</source-object-class>
    <target-object-class>userProxyFull</target-object-class>
</user-proxy>
```

---
### Lets Put it all Together:

```xml
<?xml version="1.0"?>
<doc>
 <configuration>
  <description>MacBytes User Sync</description>
  <security-mode>object</security-mode>
  <source-ad-name>macbytes.io</source-ad-name>
  <source-ad-partition>dc=macbytes,dc=io</source-ad-partition>
  <source-ad-account>thatmacadmin</source-ad-account>
  <account-domain>macbytes</account-domain>
  <target-dn>dc=jss,dc=macbytes,dc=io</target-dn>
  <query>
   <base-dn>ou=Users,ou=Users and Groups,dc=macbytes,dc=io</base-dn>
   <base-dn>ou=Application Groups,ou=Users and Groups,dc=macbytes,dc=io</base-dn>
   <base-dn>ou=App Grps,ou=Unix,dc=macbytes,dc=io</base-dn>
   <object-filter>(&#124;(objectCategory=Person)(objectCategory=OrganizationalUnit)(objectCategory=Group))</object-filter>
   <attributes>
    <include>userPrincipalName</include>
    <include>title</include>
    <include>sAMAccountName</include>
    <include>uid</include>
    <include>cn</include>
    <include>sn</include>
    <include>streetAddress</include>
    <include>telephoneNumber</include>
    <include>givenName</include>
    <include>member</include>
    <exclude></exclude>
   </attributes>
  </query>
  <schedule>
   <aging>
    <frequency>0</frequency>
    <num-objects>0</num-objects>
   </aging>
   <schtasks-cmd></schtasks-cmd>
  </schedule>
  <user-proxy>
    <source-object-class>user</source-object-class>
    <target-object-class>userProxyFull</target-object-class>
  </user-proxy>
 </configuration>
 <synchronizer-state>
  <dirsync-cookie></dirsync-cookie>
  <status></status>
  <authoritative-adam-instance></authoritative-adam-instance>
  <configuration-file-guid></configuration-file-guid>
  <last-sync-attempt-time></last-sync-attempt-time>
  <last-sync-success-time></last-sync-success-time>
  <last-sync-error-time></last-sync-error-time>
  <last-sync-error-string></last-sync-error-string>
  <consecutive-sync-failures></consecutive-sync-failures>
  <user-credentials></user-credentials>
  <runs-since-last-object-update></runs-since-last-object-update>
  <runs-since-last-full-sync></runs-since-last-full-sync>
 </synchronizer-state>
</doc>
```
