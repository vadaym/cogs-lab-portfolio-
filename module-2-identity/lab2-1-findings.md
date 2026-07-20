<h1 align=center>Mapping LDAP concepts to InstaSafe AD Sync</h1>

| LDAP Concept          | What it means                                                                         | Example                                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Base DN**           | Starting point where InstaSafe searches for users and groups.                         | `dc=lab,dc=instasafe,dc=local` or `ou=People,dc=lab,dc=instasafe,dc=local`                                 |
| **Bind DN**           | Service account (or user) used by InstaSafe to authenticate to LDAP before searching. | `cn=admin,dc=lab,dc=instasafe,dc=local` or `uid=ldap-sync,ou=ServiceAccounts,dc=lab,dc=instasafe,dc=local` |
| **Bind Password**     | Password for the Bind DN.                                                             | `********`                                                                                                 |
| **User Search Base**  | OU where user objects are located.                                                    | `ou=People,dc=lab,dc=instasafe,dc=local`                                                                   |
| **Group Search Base** | OU where groups are located.                                                          | `ou=Groups,dc=lab,dc=instasafe,dc=local`                                                                   |
| **User Filter**       | LDAP filter used to locate users.                                                     | `(objectClass=inetOrgPerson)` or `(&(objectClass=user)(objectCategory=person))` for Active Directory       |
| **Login Attribute**   | Attribute users enter as their username.                                              | `uid`, `sAMAccountName`, or `userPrincipalName`                                                            |
| **Email Attribute**   | Email address attribute.                                                              | `mail`                                                                                                     |
| **Display Name**      | User's full name.                                                                     | `cn` or `displayName`                                                                                      |
| **Group Membership**  | Attribute that indicates group membership.                                            | `memberOf`, `member`, or `uniqueMember`                                                                    |

# What does a support engineer do when they see LDAP Error 49 in an AD Sync log?

LDAP Error 49 means authentication (bind) failed. The first priority is to determine why the bind failed.

- Verify LDAP server is reachable.
- Test the Bind DN with ldapwhoami.
- If Error 49 occurs, inspect the AD diagnostic sub-code (if available).
- Confirm the bind account's password and status.
- Verify the Base DN and search filters.
- Test user searches with ldapsearch.
- Trigger the AD sync again and review the logs for successful binds and returned user entries.

This structured approach helps isolate whether the failure is due to authentication, directory configuration, or search settings.
