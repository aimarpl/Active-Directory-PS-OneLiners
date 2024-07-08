## AD Security

Find computer accounts inactive for more than 180 days
```
Search-ADaccount -ComputersOnly -AccountInactive -Timespan 180
```
Find user accounts with empty password allowed
```
get-adobject -ldapfilter "(&(objectCategory=person)(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=32))" -properties useraccountcontrol
```
Get all accounts with PasswordNeverExpires enabled
```
Search-ADAccount -PasswordNeverExpires | ft samaccountname,name,enabled
```
Get all groups with admincount set to 1 (administrative rights)
```
Get-ADGroup –LDAPFilter “(admincount=1)”
```
Get all servers with specified operating system version
```
Get-ADComputer -Filter {OperatingSystem -Like "Windows Server 2008*"} -Property * | Format-Table Name,OperatingSystem,OperatingSystemServicePack,OperatingSystemVersion -Wrap -Auto
```
Get SPNs assigned to users / kerberoasting
```
dsquery * "dc=domain,dc=com" -filter "(&(objectcategory=user)(servicePrincipalName=*))" -attr distinguishedName servicePrincipalName
```
