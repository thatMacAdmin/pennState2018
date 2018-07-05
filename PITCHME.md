---?color=#FF9B52
### Get Schema Diffs from AD to AD LDS

---
### Getting your PROD AD Schema
<div style="text-align: left">
We need this in order to compare it with your current AD LDS schema so we can get the diffs.<br/>
Replace DC=myADServer01,DC=io with the distinguished name of your AD server root.<br/>
</div>
```

ldifde -f myProdADSchema.ldif -d CN=Schema,CN=Configuration,DC=macbytes,DC=io

```

---
### Now Get Your Diffs:
Open
```
C:\WINDOWS\ADAM\ADSchemaAnalyzer.exe
```

Now we will load up the target schema that we extracted
- File -> Load Target Schema -> Load LDIF

Next we will
- File -> Load Base Schema -> Enter your AD LDS Server Information

Now setup for export
- Schema -> Mark all non-present elements as included

Finally
- File -> Create LDIF File

---
### Lets import the diffs:

```
ldifde -i -f myMissingElements.ldf -c dc=X DC=jss,DC=macbytes,DC=io
```

---
