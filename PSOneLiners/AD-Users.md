## AD User management

### Get count of all users in AD
```
get-adobject -SearchBase "DC=domain,DC=com" -Filter {(objectClass -eq "user") -and (enabled -eq $true)} -SearchScope Subtree | Measure-Object
```

Add user to a group for period of time (time based group membership)
```
Add-ADGroupMember -Identity 'GroupName' -Members 'AccountName' -MemberTimeToLive (New-TimeSpan -Minutes 15)
```
Check remaining time based group membership
```
Get-ADGroup 'GroupName' -Property member -ShowMemberTimeToLive
```
Copy groups from one user to another
```
Get-ADUser -Identity SourceUser -Properties memberof | Select-Object -ExpandProperty memberof | Add-ADGroupMember -Members TargetUser -PassThru | Select-Object -Property SamAccountName
```

Get all enabled user accounts from specified group
```
Get-AdGroupMember -identity 'GroupName' | get-aduser | Where {$_.Enabled -eq $true}
```
Get user password expiration date
```
Get-ADUser UserName –Properties DisplayName, msDS-UserPasswordExpiryTimeComputed | Select-Object -Property Displayname,@{Name="ExpiryDate";Expression={[datetime]::FromFileTime($_."msDS-UserPasswordExpiryTimeComputed")}}
```

### Account Lockouts
Find AD users that were locked out within last X days
```
Search-ADAccount -lockedout | where-object {($_.enabled -eq 'True') -and ($_.LastLogonDate -lt (Get-Date).AddDays(-3))} # | unlock-adaccount 
```


### Mail related user activities
Find AD user with specific proxyAddresses configured
```
Get-AdUser -Filter * -Properties ProxyAddresses | where-object {$_.ProxyAddresses -like '*user@domain.com*'}
```


