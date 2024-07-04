# Basics

- Powershell is the Windows scripting language and shell environment
- Powershell is built using the .NET framework

## cmdlets

### Overview

- Most Powershell commands are called **cmdlets**
    - The output of cmdlets are objects
- Running cmdlets allows you to perform actions on the output object (which makes it convenient to pass output from one cmdlet to another)
- The normal format of a cmdlet **is represented using **Verb-Noun**; for example, the cmdlet to list commands is called `Get-Command`
    - Common verbs are:
        - Get
        - Start
        - Stop
        - Read
        - Write
        - New
        - Out

### Get-Help & Get-Command

- `Get-Help` displays information about a cmdlet*.* To get help with a particular command, run the following: `Get-Help Command-Name`
- Pass the `-examples` flag to commands to understand exactly how to use the command
- `Get-Command` gets all the cmdlets **installed on the current Computer
    - It allows for pattern matching like the following: `Get-Command Verb-*` or `Get-Command *-Noun`

### Object Manipulation

- cmdlets return objects (which contain methods and properties); to manipulate the output, there are 2 options:
    - pass the output to another cmdlet (with the Pipeline `|`)
    - use specific object cmdlets to extract information
- To check methods of an object returned by a cmdlet: `Get-Command | Get-Member -MemberType Method`
- The `Select-Object` cmdlet is used to create a new object from properties pulled out of the output of another cmdlet
    - Flags:
        - `first` - gets the first x object
        - `last` - gets the last x object
        - `unique` - shows the unique objects
        - `skip` - skips x objects
