# Locked-out-users



## Lock out event

### Please enter the user name like Test NOT Test@domain.com

```
$UserName = Read-Host "Please enter the user name"

$y = Get-ADDomainController -Filter *
foreach($j in $y){

#$x = Get-EventLog -LogName Security| Where-Object {$_.EventID -eq 4740} | Where-Object {$_.ReplacementStrings[0] -eq $UserName}
$x = Get-EventLog -ComputerName $j.Name -LogName Security | Where-Object {$_.EventID -eq 4740} | Where-Object {$_.ReplacementStrings[0] -eq $UserName}

  foreach($i in $x){

Write-Host "User name "($i.ReplacementStrings.Get(0))" has locked from computer "($i.ReplacementStrings.Get(1))" at "($i.TimeGenerated) –ForegroundColor Green

  }
}
```
