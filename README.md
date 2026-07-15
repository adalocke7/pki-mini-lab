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

## Screenshots
File directory and pathway setup
<img width="576" height="42" alt="image" src="https://github.com/user-attachments/assets/9722cf8f-ca4d-42e5-8179-35e6ec9398b6" />

Creating and editing the CA config file
<img width="953" height="1040" alt="image" src="https://github.com/user-attachments/assets/bb25e917-983e-4ab9-b1f6-52af6725ff2d" />


