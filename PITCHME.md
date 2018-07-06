---?color=#FF9B52
### Configuration for AD LDS
#### Code Examples

---?color=#E864AB
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

---?color=#74992e
### Tell ADAM What to Sync:

```xml
<base-dn>ou=Users and Groups,dc=macbytes,dc=io</base-dn>
```
Note: You have to specify a fairly base DN here as if you specify one that is a child of a child, you will have issues with syncing and you will get some infinite recursion issues.

---?color=#1598FF
### Set Object Filter:

```xml
<object-filter>(&#124;(objectCategory=Person)(objectCategory=OrganizationalUnit)(objectCategory=Group))</object-filter>
```
---?color=#FF543F
### Configure Sync Attributes
```xml
<attributes>
    <include>objectSID</include>
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

---?color=#FF9B52
### Get User-Object-Proxy Working:

```xml
<user-proxy>
    <source-object-class>user</source-object-class>
    <target-object-class>userProxyFull</target-object-class>
</user-proxy>
```
