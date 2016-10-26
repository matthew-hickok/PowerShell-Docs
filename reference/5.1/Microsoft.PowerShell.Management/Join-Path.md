﻿---
author: jpjofre
description: 
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell, cmdlet
manager: carolz
ms.date: 2016-10-11
ms.prod: powershell
ms.technology: powershell
ms.topic: reference
online version: http://go.microsoft.com/fwlink/?LinkId=822245
schema: 2.0.0
title: Join-Path
---

# Join-Path

## SYNOPSIS
Combines a path and a child path into a single path.

## SYNTAX

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## DESCRIPTION
The **Join-Path** cmdlet combines a path and child-path into a single path.
The provider supplies the path delimiters.

## EXAMPLES

### Example 1: Combine a path with a child path
```
PS C:\>Join-Path -Path "C:\win*" -ChildPath "System*"
```

This command uses **Join-Path** to combine the C:\Win* path with the System* child path.
The Windows PowerShell file system provider, FileSystem joins the path and adds the "\" delimiter.

### Example 2: Display files and folders by joining a path with a child path
```
PS C:\>Join-Path "C:\win*" "System*" -Resolve
```

This command displays the files and folders that are referenced by joining the C:\Win* path and the System* child path.
It displays the same files and folders as Get-ChildItem, but it displays the fully qualified path to each item.
In this command, the *Path* and *ChildPath* optional parameter names are omitted.

### Example 3: Use Join-Path with the Windows PowerShell registry provider
```
PS C:\>
PS HKLM:\> Join-Path System *ControlSet* -Resolve
```

This command displays the registry keys in the HKLM\System registry subkey that include ControlSet.
The command shows how to use **Join-Path** with the Windows PowerShell registry provider.

### Example 4: Combine multiple path roots with a child path
```
PS C:\>Join-Path -Path C:, D:, E:, F: -ChildPath New
```

This command uses **Join-Path** to combine multiple path roots with a child path.

### Example 5: Combine the roots of a file system drive with a child path
```
PS C:\>Get-PSDrive -PSProvider filesystem | ForEach {$_.root} | Join-Path -ChildPath "Subdir"
```

This command combines the roots of each Windows PowerShell file system drive in the console with the Subdir child path.

The command uses the Get-PSDrive cmdlet to get the Windows PowerShell drives supported by the FileSystem provider.
The ForEach-Object statement selects only the Root property of the **PSDriveInfo** objects and combines it with the specified child path.

The output shows that the Windows PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.

## PARAMETERS

### -ChildPath
Specifies the elements to append to the value of the *Path* parameter.
Wildcards are permitted.
The *ChildPath* parameter is required, although the parameter name ("ChildPath") is optional.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential
Specifies a user account that has permission to perform this action.
The default is the current user.

Type a user name, such as User01 or Domain01\User01.
Or, enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers installed with Windows PowerShell.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path
Specifies the main path (or paths) to which the child-path is appended.
Wildcards are permitted.

The value of *Path* determines which provider joins the paths and adds the path delimiters.
The *Path* parameter is required, although the parameter name ("Path") is optional.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Resolve
Indicates that this cmdlet displays the items that are referenced by the joined path.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction
Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String
You can pipe a string that contains a path to this cmdlet.

## OUTPUTS

### System.String
This cmdlet returns a string that contains the resulting path.

## NOTES
* The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all Windows PowerShell providers can interpret. They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format. Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.

  You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.

  This cmdlet is designed to work with the data exposed by any provider.
To list the providers available in your session, type `Get-PSProvider`.
For more information, see about_Providers.

*

## RELATED LINKS

[Convert-Path](Convert-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-PSDrive](Get-PSDrive.md)
