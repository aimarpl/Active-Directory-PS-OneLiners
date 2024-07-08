## AD Health
Get all domain controllers
```
Get-ADDomainController –Filter * | Select Hostname, IsGlobalCatalog
```
