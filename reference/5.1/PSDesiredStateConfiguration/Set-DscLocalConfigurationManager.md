---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
---
# Set-DscLocalConfigurationManager

## SYNOPSIS

Applies Local Configuration Manager (LCM) settings to nodes.

## SYNTAX

### ComputerNameSet (Default)

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

The `Set-DscLocalConfigurationManager` cmdlet applies LCM settings,
or meta-configuration, to nodes. Specify computers by specifying computer names or by using Common
Information Model (CIM) sessions. If you do not specify a target computer, the cmdlet applies
settings to the local computer.

## EXAMPLES

### Example 1: Apply LCM settings

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

This command applies the LCM settings from `C:\DSC\Configurations\` to the targeted nodes. After
receiving the settings, LCM processes them.

> [!WARNING]
> If there are multiple meta mofs for the same computer stored in the specified folder, only the
> first meta mof will be applied.

### Example 2: Apply LCM settings by using a CIM session

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

This example applies LCM settings to a computer and applies the settings. The example creates a CIM
session for a computer named Server01 for use with the cmdlet. Alternatively, create an array of CIM
sessions to apply the cmdlet to multiple specified computers.

The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the
**CimSession** object in the `$Session` variable. The command prompts you for a password. For more
information, type `Get-Help New-CimSession`.

The second command applies LCM settings for the targeted node from `C:\DSC\Configurations\` to the
computer identified by the **CimSession** objects stored in the `$Session` variable. In this example,
the `$Session` variable contains a CIM session only for the computer named Server01. The command
applies the settings. After receiving the settings, LCM processes them.

## PARAMETERS

### -CimSession

Runs the cmdlet in a remote session or on a remote computer. Enter a computer name or a session
object, such as the output of a [New-CimSession](/powershell/module/CimCmdlets/New-CimSession)
or [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.
The default is the current session on the local computer.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

Specifies an array of computer names. This parameter restricts the computers that have
meta-configuration documents in the **Path** parameter to those specified in the array.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential

Specifies a user name and password, as a **PSCredential** object, for the target computer. To obtain
a **PSCredential** object, use the Get-Credential cmdlet. For more information, type
`Get-Help Get-Credential`.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Forces the command to run without asking for user confirmation.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Specifies a file path of a folder that contains configuration settings files. The cmdlet publishes
and applies these LCM settings to computers that have settings files in the specified path. Each
target node must have a settings file of the following format: `NetBIOS Name.meta.mof`.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Specifies the maximum number of concurrent operations that can be established to run the cmdlet. If
this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an
optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the
computer. The throttle limit applies only to the current cmdlet, not to the session or to the
computer.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Prompts you for confirmation before running the cmdlet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable,
-InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose,
-WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview)

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)
