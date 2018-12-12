﻿# Grant-HypSecurityGroupIngress

   Adds an ingress rule to a security group.

## Syntax
```
Grant-HypSecurityGroupIngress [-LiteralPath] <String> -GroupId <String[]> -Protocol <String> [-FromPort <Decimal>] [-ToPort <Decimal>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Grant-HypSecurityGroupIngress [-LiteralPath] <String> -IPRange <String[]> -Protocol <String> [-FromPort <Decimal>] [-ToPort <Decimal>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Adding an egress rule permits network traffic from source CIDR IP address ranges or security groups to pass to instances within a security group.

## Related Commands
  * [Amazon AuthorizeSecurityGroupEgress: http://docs.aws.amazon.com/AWSEC2/latest/APIReference/ApiReference-query-AuthorizeSecurityGroupEgress.html](Amazon AuthorizeSecurityGroupEgress: http://docs.aws.amazon.com/AWSEC2/latest/APIReference/ApiReference-query-AuthorizeSecurityGroupEgress.html.html)
  * [IANA protocol numbers: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml](IANA protocol numbers: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml.html)
  * [Grant-HypSecurityGroupEgress](Grant-HypSecurityGroupEgress.html)
  * [Revoke-HypSecurityGroupIngress](Revoke-HypSecurityGroupIngress.html)
  * [Revoke-HypSecurityGroupEgress](Revoke-HypSecurityGroupEgress.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the full XDHyp provider path to the security group, equivalent to the FullPath property of the security group object. The path can specify a security group relative to a hypervisor conection or hosting unit. | true | true (ByValue) |  |
| Protocol | Specifies the protocol name or number. Protocol numbers can be found at: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml<br>Use -1 to specify all protocols. | true | false |  |
| GroupId | Specifies one or more source security groups from which traffic will be permitted by this rule. This parameter cannot be specified in conjunction with IPRange. | true | false |  |
| IPRange | Specifies one or more source CIDR IP address ranges from which traffic will be permitted by this rule. This parameter cannot be specified in conjunction with IPRange. | true | false |  |
| FromPort | The start of the port range for port based protocols. For ICMP this specifies the type number.<br>Use -1 to specify all ICMP types. | false | false | 0 |
| ToPort | The end of the port range for port based protocols. For ICMP this specifies the type number, where -1 can be used to specify all ICMP types. | false | false | 0 |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### System.string
   The LiteralPath can be piped in.
## Return Values
### None
   ## Notes
   Security groups can be added and removed using the New-Item and Remove-Item cmdlets.
## Examples

### EXAMPLE 1
```
c:\PS> $Group = New-Item -ItemType SecurityGroup -Path XDHyp:\Connections\AWS -Name MySecurityGroup -Description 'Example group'
          c:\PS> Grant-HypSecurityGroupIngress $Group.FullPath -FromPort 80 -ToPort 80 -Protocol tcp -IPRange '0.0.0.0/0'
```
   Description<br>-----------<br>Create a security group and grant ingress on port 80 from anywhere.
### EXAMPLE 2
```
c:\PS> $Group1 = New-Item -ItemType SecurityGroup -Path XDHyp:\Connections\AWS -Name MySecurityGroup1 -Description 'Example group 1'
          c:\PS> $Group2 = New-Item -ItemType SecurityGroup -Path XDHyp:\Connections\AWS\MySecurityGroup2 -Description 'Example group 2'
          c:\PS> Grant-HypSecurityGroupEgress $Group1.FullPath -FromPort 8080 -ToPort 8080 -Protocol tcp -GroupId $Group2.Id
          c:\PS> Grant-HypSecurityGroupIngress $Group2.FullPath -FromPort 8080 -ToPort 8080 -Protocol tcp -GroupId $Group1.Id
          c:\PS> Grant-HypSecurityGroupEgress $Group2.FullPath -Protocol '-1' -GroupId $Group1.Id
          c:\PS> Grant-HypSecurityGroupIngress $Group1.FullPath -Protocol '-1' -GroupId $Group2.Id
```
   Description<br>-----------<br>Make 2 security groups and permit group 1 access to group 2 only on port 8080 while granting full access to group 1 from group 2.
