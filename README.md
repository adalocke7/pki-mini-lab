# Mini PKI Lab

## Overview
This mini project is a home lab Public Key Infrastructure(PKI) using OpenSSL to apply knowledge from Topic 1 of CompTIA Security+. The project demonstrates the construction of a root Certificate Authority(CA), an intermediate CA, key pairs, and signed certificates resulting in a browser-trusted HTTPS server with a valid signed certificate from the intermediate CA.

## What I Learned / Concepts Demonstrated
- Asymmetric encryption (public/private key pairs)
- Certificate chain of trust (root CA → intermediate CA → server cert)
- CA configuration files
- X.509 certificate structure
- HTTPS/TLS deployment
- Linux/openssl commands
- Nginx server configuration and TLS deployment

## Architecture
[Simple diagram: Root CA -> Intermediate CA -> Server Cert -> HTTPS server]
(Even a basic diagram made in draw.io or excalidraw helps a lot visually)

## Steps Taken
1. Generated root CA key and self-signed cert
  - 4096-bit RSA key, AES256 encryption.
  - Configured policy_strict for root-level signing rules.
2. Generated intermediate CA, signed by root
  - Created CSR, signed with root CA using v3_intermediate_ca extension.
  - Verified patlen:0 constraint to prevent further sub-CA's
3. Generated server key + CSR
  - 2048-bit RSA key
4. Signed server cert with intermediate CA
  - Verified common name and subject alternative name to comply with modern browser certification validation rules.
5. Deployed cert on Nginx for local HTTPS

## Challenges / Troubleshooting
- Config path mismatch and duplicate: Both Root and intermediate OpenSSL.cnf still referenced the default '/root/ca' path, which caused "could not open file" errors. This was fixed by updating the 'dir =' to the full project path. Additionally, even after changing the directory path, it still caused the same error due to having the same CA_default pasted twice, which was quickly fixed by deleting the duplicate config.

- Chrome "Not Secure" despite trusted root CA: The certificate for the server showed a valid chain, but Chrome still flagged it as "Not Secure". After troubleshooting by looking at both Windows and Chrome's Trusted Certification files, the root cause was modern browsers requiring a Subject Alternative Name (SAN) extension that explicitly lists the hostname, as just a CN field was not adequate anymore for trusted certificates. Fixed by adding a subjectAltName extension to the server cert configuration and reissuing the certificate.

- Duplicate certificate subject error: Reissuing the server cert with an updated SAN fix caused an error because OpenSSL's CA rejected a second certificate that had an identical subject by default. Fixed by setting 'unique_subject = no' in the intermediate CA's index.txt.attr file and adding it to the intermediate openssl.cnf config.

## Screenshots
File directory and pathway setup
<img width="576" height="42" alt="image" src="https://github.com/user-attachments/assets/9722cf8f-ca4d-42e5-8179-35e6ec9398b6" />

Creating and editing the CA config file
<img width="953" height="1040" alt="image" src="https://github.com/user-attachments/assets/bb25e917-983e-4ab9-b1f6-52af6725ff2d" />

Creating the private key and a certificate signing request for the intermediate CA
<img width="933" height="557" alt="image" src="https://github.com/user-attachments/assets/2e02fbca-b579-4d9f-bce8-ee3755df184d" />

Signing the intermediate CA with the root CA
<img width="1919" height="533" alt="image" src="https://github.com/user-attachments/assets/082f914c-4d82-441d-8210-bf8f254d1534" />

Verifying the intermediate CA signature matches the root CA
<img width="1281" height="34" alt="image" src="https://github.com/user-attachments/assets/3d599a4d-8777-4789-aa72-1f15aa2e4960" />

Creating and signing a server certificate with the intermediate CA
<img width="1912" height="632" alt="image" src="https://github.com/user-attachments/assets/150f6091-0208-49e0-b00b-84ed83b505bf" />

Verifying the Nginx localhost server, which verifies the certificate chain of trust.
<img width="989" height="883" alt="image" src="https://github.com/user-attachments/assets/2742dcae-064f-4792-995f-3ee8dcae432d" />

Fully deployed Nginx server on Chrome with valid and accepted certification
<img width="1503" height="936" alt="image" src="https://github.com/user-attachments/assets/2798ba89-abc9-47cc-b0c1-858e4be284fa" />







