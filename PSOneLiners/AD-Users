## AD User management

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
```
Get all enabled user accounts from specified group
```
Get-AdGroupMember -identity 'GroupName' | get-aduser | Where {$_.Enabled -eq $true}
```
Get user password expiration date
```
Get-ADUser UserName –Properties DisplayName, msDS-UserPasswordExpiryTimeComputed | Select-Object -Property Displayname,@{Name="ExpiryDate";Expression={[datetime]::FromFileTime($_."msDS-UserPasswordExpiryTimeComputed")}}
```
