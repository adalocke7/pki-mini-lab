# Mini PKI Lab

## Overview
1-2 sentences: what this project does and why you built it 
(e.g. "Built to apply PKI concepts from CompTIA Security+ in a hands-on environment")

## What I Learned / Concepts Demonstrated
- Asymmetric cryptography (public/private key pairs)
- Certificate chain of trust (root CA → intermediate CA → server cert)
- X.509 certificate structure
- HTTPS/TLS deployment

## Architecture
[Simple diagram: Root CA -> Intermediate CA -> Server Cert -> HTTPS server]
(even a basic diagram made in draw.io or excalidraw helps a lot visually)

## Steps Taken
1. Generated root CA key and self-signed cert
2. Generated intermediate CA, signed by root
3. Generated server key + CSR
4. Signed server cert with intermediate CA
5. Deployed cert on Nginx for local HTTPS

## Commands Used
(brief, annotated — not just a wall of commands)

## Challenges / Troubleshooting
(this section is underrated — shows real problem-solving, not just a tutorial follow-along)

## Screenshots
(browser showing the cert chain, terminal output, etc.)
