FSMO - Get DomainNamingMaster and SchemaMaster role holders
```
Get-ADForest domain.com | fl DomainNamingMaster, SchemaMaster
```
FSMO - Get InfrastructureMaster, PDCEmulator and RIDMaster role holders
```
Get-ADDomain domain.com | fl InfrastructureMaster, PDCEmulator, RIDMaster
```
FSMO - Move role
```
Move-ADDirectoryServerOperationMasterRole -Identity "New-Host" RoleName
```
