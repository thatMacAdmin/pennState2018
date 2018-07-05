---
### Pushing the big button!

---
### But first lets install the schema
----
```shell
C:\Windows\ADAM\adamsync.exe /install localhost:389 C:\Some\XML\Location\customAdamsync.xml
```

---
### Now - We Sync!
----
```shell
C:\Windows\ADAM\adamsync.exe /sync localhost:389 “DC=jss,DC=macbytes,DC=io” /log C:\Some\Log\Location\adamsync.log
```

