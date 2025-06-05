We can enumerate ACL with tools such as [[BloodHound]] or PowerView, and abused with PowerView.

Some examples permissions:
- `ForceChangePassword` abused with `Set-DomainUserPassword`
- `Add Members` abused with `Add-DomainGroupMember`
- `GenericAll` abused with `Set-DomainUserPassword` or `Add-DomainGroupMember`
- `GenericWrite` abused with `Set-DomainObject`
- `WriteOwner` abused with `Set-DomainObjectOwner`
- `WriteDACL` abused with `Add-DomainObjectACL`
- `AllExtendedRights` abused with `Set-DomainUserPassword` or `Add-DomainGroupMember`
- `Addself` abused with `Add-DomainGroupMember`

## ACEs breakdown

#### ForceChangePassword
Right to reset user's password without first knowing it

#### GenericWrite
Can write to any non-protected attribute on an object. We can for example assign them a SPN to then perform kerberoasting.
Access to a computer object could lead to Resource-Based contrained delegation attack

#### GenericAll
Can do anything to an object (change password, change group, ...)


![[ACL.png]]