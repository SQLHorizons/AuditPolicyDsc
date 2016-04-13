# xAuditPolicy

The **xAuditPolicy** DSC resources allow you to configure and manage the advanced audit policy in Windows.

# Description

The **xAuditPolicy** module contains the **xAuditCategory** and **xAuditOption** DSC Resources. These DSC Resources allow you to configure the advanced audit policies in all currently supported versions of Windows.

## Contributing
Please check out common DSC Resources [contributing guidelines](https://github.com/PowerShell/DscResource.Kit/blob/master/CONTRIBUTING.md).

# Resources

* **xAuditCategory** configures the advanced audit policy Subcategories audit flags. 

* **xAuditOption** manages the auditpol options available in the auditpol.exe utility. 


## xAuditCategory
* **Subcategory:** Name of the subcategory in the advanced audit policy.

* **AuditFlag:** The name of the audit flag to apply to the subcategory. This is can be either Success or Failure.

## xAuditOption

 * **Name:** The name of the option to configure. 
 
 * **Vaule:** The value to apply to the option. This can be either Enabled or Disabled. 
 
# Versions

## Unreleased

## 1.0.0.0
* Initial release with the following resources:

  * xAuditPolicy 
  * xAuditOption   

# Examples

Example 1 Audit Logon Success and Failure
```powershell
    # A configuration to audit Logon Failure but not Success
    Configuration AuditPolicy
    {
        Import-DscResource -ModuleName xAuditPolicy

        xAuditCategory LogonSuccess
        {
            Subcategory = 'Logon'
            AuditFlag   = 'Success'
            Ensure      = 'Present' 
        } 

        xAuditCategory LogonFailure
        {
            Subcategory = 'Logon'
            AuditFlag   = 'Failure'
            Ensure      = 'Present' 
        } 
    }
```

Example 2 Audit Logon Failure only
```powershell
    # A configuration to audit Logon Failure but not Success
    Configuration AuditPolicy
    {
        Import-DscResource -ModuleName xAuditPolicy

        xAuditCategory LogonSuccess
        {
            Subcategory = 'Logon'
            AuditFlag   = 'Success'
            Ensure      = 'Absent' 
        } 

        xAuditCategory LogonFailure
        {
            Subcategory = 'Logon'
            AuditFlag   = 'Failure'
            Ensure      = 'Present' 
        } 
    }
```