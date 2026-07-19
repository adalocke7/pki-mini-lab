# Mini PKI Lab

## Overview
This mini project is a home lab Public Key Infrastructure(PKI) using OpenSSL to apply knowledge from Topic 1 of CompTIA Security+. The project demonstrates the construction of a root Certificate Authority(CA), an intermediate CA, key pairs, and signed certificates.

## What I Learned / Concepts Demonstrated
- Asymmetric encryption (public/private key pairs)
- Certificate chain of trust (root CA → intermediate CA → server cert)
- CA configuration files
- X.509 certificate structure
- HTTPS/TLS deployment
- Basic bash/shell commands

## Architecture
[Simple diagram: Root CA -> Intermediate CA -> Server Cert -> HTTPS server]
(Even a basic diagram made in draw.io or excalidraw helps a lot visually)

## Steps Taken
1. Generated root CA key and self-signed cert
2. Generated intermediate CA, signed by root
3. Generated server key + CSR
4. Signed server cert with intermediate CA
5. Deployed cert on Nginx for local HTTPS

## Commands Used
- openssl genrsa ... - The openssl command used to generate the private keys for the root CA and intermediate CA.
- chmod ### - Used to specify the security clearance for the specified file/directory, specifying read/write/execute access and who has access.
- 

## Challenges / Troubleshooting
Troubleshot the Linux system and commands due to Linux being a new system and having no prior knowledge of Linux operations.
Troubleshot setting up the Nginx server to deploy a server certificate.

## Screenshots
File directory and pathway setup
<img width="576" height="42" alt="image" src="https://github.com/user-attachments/assets/9722cf8f-ca4d-42e5-8179-35e6ec9398b6" />

Creating and editing the CA config file
<img width="953" height="1040" alt="image" src="https://github.com/user-attachments/assets/bb25e917-983e-4ab9-b1f6-52af6725ff2d" />

Creating the private key and a certificate signing request for the intermediate CA
<img width="933" height="557" alt="image" src="https://github.com/user-attachments/assets/2e02fbca-b579-4d9f-bce8-ee3755df184d" />

Signing the intermediate CA with the root CA
<img width="1919" height="533" alt="image" src="https://github.com/user-attachments/assets/082f914c-4d82-441d-8210-bf8f254d1534" />

Verifying the intermediate CA signiture matches with the root CA
<img width="1281" height="34" alt="image" src="https://github.com/user-attachments/assets/3d599a4d-8777-4789-aa72-1f15aa2e4960" />

Creating and signing a server certificate with the intermediate CA
<img width="1912" height="632" alt="image" src="https://github.com/user-attachments/assets/150f6091-0208-49e0-b00b-84ed83b505bf" />

Verifying the Nginx localhost server, which verifies the certificate chain of trust.
<img width="989" height="883" alt="image" src="https://github.com/user-attachments/assets/2742dcae-064f-4792-995f-3ee8dcae432d" />






