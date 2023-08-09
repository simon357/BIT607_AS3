# BIT607_AS3
Copy of code from Assessment 2 to be modified during Assessment 3

https://learn.microsoft.com/en-us/powershell/scripting/learn/deep-dives/everything-about-arrays?view=powershell-7.3

https://serverfault.com/questions/532945/list-all-groups-and-their-members-with-powershell-on-win2008r2

https://learn.microsoft.com/en-us/powershell/module/exchange/get-mailboxpermission?view=exchange-ps
Get-MailboxPermission -Identity Room222 -Owner

-ResultSize Unlimited

-Identity
The Identity parameter specifies the mailbox you want to view. You can use any value that uniquely identifies the mailbox. For example:

Name
Alias
Distinguished name (DN)
Canonical DN
Domain\Username
Email address
GUID
LegacyExchangeDN
SamAccountName
User ID or user principal name (UPN)

https://activedirectorypro.com/list-ntfs-permissions-all-folders/#:~:text=To%20get%20NTFS%20folder%20permissions,to%20the%20get%2Dacl%20command.

Get-ChildItem -Directory -Path "\\srv-vm1\share" -Recurse -Force | get-acl | format-list | out-file c:\it\ntfs-report.txt


https://techcommunity.microsoft.com/t5/microsoft-365/listing-shared-mailboxes-and-members-powershell/m-p/241737

Get-Mailbox -RecipientTypeDetails SharedMailbox -ResultSize:Unlimited | Get-MailboxPermission | select identity,user,accessrights  | where { ($_.User -like '*@*')   }

SendAs example
Get-RecipientPermission -Identity "mailbox" -AccessRights sendas | where {($_.trustee -like '*@*') }
