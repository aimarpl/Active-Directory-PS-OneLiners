## AD Health
Get all domain controllers
```
Get-ADDomainController –Filter * | Select Hostname, IsGlobalCatalog
```

Find inbound replication partners for a given domain controller
```
Get-ADReplicationPartnerMetadata -Target "dc01.domain.com"
```

List all the inbound replication partners for given domain
```
Get-ADReplicationPartnerMetadata -Target "domain.com" -Scope Domain
```

List replication failures for a site, forest, domain, domain controller
```
Get-ADReplicationFailure -Target "dc01.domain.com"
```

List replication failures for a domain
```
Get-ADReplicationFailure -Target "domain.com" -Scope Domain
```

List replication failures for forest
```
Get-ADReplicationFailure -Target "domain.com" -Scope Forest
```

List replication failures for site
```
Get-ADReplicationFailure -Target "Default-First-Site-Name" -Scope Site
```
