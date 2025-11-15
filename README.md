# n8n Deployment with Custom SSL Certificate

## Overview

By default, when setting up an n8n instance following the official [documentation](https://docs.n8n.io/hosting/installation/server-setups/docker-compose/), the Traefik reverse proxy container will attempt to automatically obtain an SSL/TLS certificate via Let’s Encrypt for the domain specified in the `.env` file.

However, in certain environments — such as internal networks that utilize non-public domain names (e.g., `.local`, `.dc`, or other private DNS namespaces) — Let’s Encrypt cannot issue certificates for these domains.

This repository provides a Docker Compose configuration that enables Traefik to use a **custom SSL certificate** instead of one issued by Let’s Encrypt. This is particularly useful when using certificates signed by an internal Certificate Authority (CA), such as an Active Directory CA, ensuring secure HTTPS access to n8n’s web interface in on‑premises or private network setups.

## Features

- Runs n8n and Traefik using Docker Compose
- Configures Traefik to serve a user-supplied SSL certificate
- Suitable for private/internal domains and custom CA infrastructure

## Use Cases

- Internal automation platforms hosted on private networks
- Environments where certificate issuance is managed by an enterprise CA
- Domains that are inaccessible to public certificate authorities

## Directory Hierarchy

```text
n8n
└── docker-setup
    ├── certs
    │   ├── fullchain.pem
    │   └── privkey.pem
    ├── compose.yml
    ├── local-files
    └── traefik
        ├── dynamic.yml
        └── traefik.yml
```

## Deployment Instructions

Replace the example configurations and certificates in this repository with your own, then start Docker using:

```bash
docker compose up -d
```
