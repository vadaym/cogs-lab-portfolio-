# Certificate observations

| Field                   | Value                                                               |
| ----------------------- | ------------------------------------------------------------------- |
| **Subject**             | `C=IN, ST=Karnataka, L=Bangalore, O=InstaSafe Lab, CN=172.31.11.55` |
| **Issuer**              | `C=IN, ST=Karnataka, L=Bangalore, O=InstaSafe Lab, CN=172.31.11.55` |
| **Key Algorithm**       | RSA 2048-bit                                                        |
| **Signature Algorithm** | `sha256WithRSAEncryption`                                           |
| **Valid From**          | `Jul 19 09:45:58 2026 GMT`                                          |
| **Expiry Date**         | `Jul 19 09:45:58 2027 GMT`                                          |
| **Certificate Type**    | Self-signed certificate                                             |
| **CA Flag**             | `CA:TRUE`                                                           |

## Self-signed certificate

The Subject and Issuer are identical:

Subject: CN=172.31.11.55
Issuer:  CN=172.31.11.55


### Why does curl without -k fail?

A normal command:

curl https://IP_Address/

performs TLS certificate validation.

curl checks:

- Is the certificate signed by a trusted CA?
- Does the certificate name match the server being contacted?
- Is the certificate within its validity period?
- Is the certificate chain valid?

In this case, validation fails because:

Certificate is not trusted
   
The server sends a self-signed certificate

# What needs to change for normal curl to succeed?

## Option 1: Use a certificate from a trusted CA (recommended)

Replace the self-signed certificate with one issued by:

- A public CA (for internet services), or
- An internal enterprise CA (for private systems)

## Option 2: Trust the existing certificate locally

For a lab/internal environment:

- Export the certificate.
- Add it to the client machine's trusted certificate store.
- Run curl normally.

