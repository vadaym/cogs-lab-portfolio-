If SSO users are getting an Attribute Error in an application that uses Keycloak, the first thing need to check is whether the required user attribute is actually being sent in the SAML assertion or OIDC token. Most "attribute" errors are caused by a missing or incorrectly mapped attribute rather than an authentication failure.

# 1. Verify the Client's Attribute Mappers (highest priority)

Menu path:

Clients → Select Client → Client Scopes (or Mappers, depending on Keycloak version)
check for:

- Required attribute mapper exists (for example: email, username, firstName, lastName, groups, or a custom attribute).
- Correct User Attribute is selected.
- Correct Token Claim Name (OIDC) or Attribute Name (SAML).
- Mapper is enabled.
- The mapper is attached to the client through the assigned client scope.

If the application expects employee_id but Keycloak sends employeeNumber, the application may report an attribute error.

# 2. Confirm the User Actually Has the Attribute

Menu path:

Users → Select User → Attributes

Verify that:

- The required attribute exists.
- The value is populated.
- There are no spelling or case mismatches.

If the mapper points to employeeNumber but the user has no value, the claim will not be included

# 3. Check User Federation or LDAP Mapping

If users come from LDAP or Active Directory:

Menu path:

User Federation → LDAP Provider → Mappers

Verify:

- LDAP attribute is mapped correctly.
- Sync has completed successfully.
- Imported users contain the expected attributes.

A common issue is that LDAP stores employeeID while Keycloak expects employeeNumber

# 4. Review Client Protocol Configuration

Menu path:

Clients → Select Client → Settings

Confirm:

- Correct protocol (OIDC or SAML).
- Correct redirect URIs.
- Client is enabled.
- Client scopes include the scope containing the required mapper.

# 5. Check Default and Optional Client Scopes

Menu path:

Clients → Select Client → Client Scopes

Verify that:

- The scope containing the mapper is assigned.
- It is a Default Client Scope if the application expects the attribute on every login.

# 6. Review Keycloak Logs

Look for messages such as:

- mapper not found
- attribute missing
- user attribute is null
- failed to generate token
- LDAP sync errors

These can quickly indicate whether the issue is with mapping, missing data, or federation.

## Common Root Causes
- Required user attribute is empty.
- Attribute mapper references the wrong user attribute.
- Incorrect claim or attribute name expected by the application.
- Mapper not assigned through client scopes.
- LDAP attribute not synchronized.
- Application expects SAML attributes but receives OIDC claims (or vice versa).
- Case-sensitive attribute name mismatch.

