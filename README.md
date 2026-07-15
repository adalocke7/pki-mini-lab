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
(brief, annotated — not just a wall of commands)

## Challenges / Troubleshooting
Troubleshot the Linux system and commands due to Linux being a new system and having no prior knowledge of Linux operations.

## Screenshots
(browser showing the cert chain, terminal output, etc.)
