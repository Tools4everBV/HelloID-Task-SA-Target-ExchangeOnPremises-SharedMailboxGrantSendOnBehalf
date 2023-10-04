
# HelloID-Task-SA-Target-ExchangeOnPremises-SharedMailboxGrantSendOnBehalf


## Prerequisites
Before using this snippet, verify you've met with the following requirements:

- [ ] User defined variables: `$ExchangeAdminUsername`, `$ExchangeAdminPassword` and `$ExchangeConnectionUri` created in your HelloID portal. [See also Custom Variables](https://docs.helloid.com/en/variables/custom-variables.html)



## Description

This code snippet executes the following tasks:

1. Define a hash table `$formObject`. The keys of the hash table represent the properties of the `Set-Mailbox` cmdlet, while the values represent the values entered in the form.

> To view an example of the form output, please refer to the JSON code pasted below.

```json
{
    "MailboxIdentity": "TestSharedMailbox",
    "DisplayName": "TestSharedMailbox",
    "UsersToAdd": [
        {
            "UserPrincipalName": "jan@connectors.com"
        }
    ]
}
```

> :exclamation: It is important to note that the names of your form fields might differ. Ensure that the `$formObject` hashtable is appropriately adjusted to match your form fields.
> The **MailboxIdentity** can hold different values [See the Microsoft Docs page](https://learn.microsoft.com/en-us/powershell/module/exchange/set-mailbox?view=exchange-ps#-grantsendonbehalfto)


2. Constructs a PowerShell credential object from the supplied administrative username and password

3. Connects with the credentials to the Exchange on premises environment by means of the `New-PSSession` cmdlet

4. Calls the `Set-Mailbox` cmdlet and adds ExtendedRights "Send On Behalf" to the Mailbox

5. Disconnects from the Exchange session by means of the `Remove-PsSession` cmdlet