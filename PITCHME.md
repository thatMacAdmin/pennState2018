---
### Getting AD Attributes from NoMAD

---
### We need to add this to our mobileconfig
----
```xml
<key>CustomLDAPAttributes</key>
<array>
    <string>attribute01</string>
    <string>attribute02</string>
</array>
```
---
### Now we just need to query the attributes
----
Rememeber that this plist is stored in the user library!
```bash
loggedInUser=`python -c 'from SystemConfiguration import SCDynamicStoreCopyConsoleUser; import sys; username = (SCDynamicStoreCopyConsoleUser(None, None, None) or [None])[0]; username = [username,""][username in [u"loginwindow", None, u""]]; sys.stdout.write(username + "\n");'` && echo "${loggedInUser}"

defaults read "/Users/${loggedInUser}/Library/Preferences/com.trusourcelabs.NoMAD.plist" attributeHere
```

