---
### Get Schema Diffs from AD to AD LDS

---
### Getting your PROD AD Schema
----
<div style="text-align: left">
- We need this in order to compare it with your current AD LDS schema so we can get the diffs.<br /><br />
- Replace DC=myADServer01,DC=io with the distinguished name of your AD server root.<br />
</div>
<br />
```shell
ldifde -f myProdADSchema.ldif -d CN=Schema,CN=Configuration,DC=macbytes,DC=io
```

---
### Now Get Your Diffs:
----
Open:<br />
```shell
C:\WINDOWS\ADAM\ADSchemaAnalyzer.exe
```

---
### Now we will load up the target schema that we extracted<br />
----
```text
File -> Load Target Schema -> Load LDIF
```

---
Next we will<br />
----
```text
File -> Load Base Schema -> Enter your AD LDS Server Information
```

---
Now setup for export<br />
----
```text
Schema -> Mark all non-present elements as included
```

---
Finally<br />
----
```text
File -> Create LDIF File
```

---
### Lets import the diffs:<br />
----
```shell
ldifde -i -f myMissingElements.ldf -c dc=X DC=jss,DC=macbytes,DC=io
```
