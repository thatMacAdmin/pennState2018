---
### Pushing the big button!

---
### But first lets install the schema
----
```shell
Adamsync /install localhost:389 CustomAdamsync.xml
```

---
### Now - We Sync!
----
```shell
C:\Windows\ADAM\adamsync.exe /sync localhost:389 “DC=jss,DC=macbytes,DC=io” /log C:\Some\Log\Location\adamsync.log
```

