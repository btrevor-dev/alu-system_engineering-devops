# ALU System Engineering & DevOps: Load Balancer

## Description

This project builds on the web server project by introducing redundancy and load balancing. Instead of relying on a single web server, traffic is now distributed across two identical web servers (`web-01` and `web-02`) through a dedicated load balancer (`lb-01`) running HAProxy. This makes the infrastructure more resilient — if one web server goes down, the other can still handle requests — and improves capacity to handle traffic.

## Learning Objectives

By the end of this project, I am able to explain:

- What load balancing is and why it improves reliability and scalability
- How HAProxy distributes traffic across multiple backend servers
- The roundrobin load balancing algorithm
- How to add custom HTTP response headers with Nginx
- How to manage services via an init script instead of `systemctl`

## Requirements

- All scripts interpreted on Ubuntu 16.04 LTS
- Every file ends with a new line
- Every Bash script starts with `#!/usr/bin/env bash`
- The second line of every script is a comment explaining what it does
- All scripts pass Shellcheck (v0.3.7) with no errors
- All scripts are executable
- `systemctl` is never used for restarting processes — `service` is used instead

## Directory: `load_balancer`

| File | Description |
|---|---|
| `0-custom_http_response_header` | Installs Nginx and adds a custom `X-Served-By` header containing the server's hostname (run on both `web-01` and `web-02`) |
| `1-install_load_balancer` | Installs and configures HAProxy on `lb-01`, distributing traffic to `web-01` and `web-02` using the roundrobin algorithm |

## Infrastructure

| Server | Role |
|---|---|
| `web-01` | First web server, serves content via Nginx |
| `web-02` | Second web server, identical configuration to `web-01` |
| `lb-01` | Load balancer running HAProxy, routes traffic to `web-01` and `web-02` |

## Usage

Run on `web-01` and `web-02`:
```bash
sudo ./0-custom_http_response_header
```

Run on `lb-01`:
```bash
sudo ./1-install_load_balancer
```

Verify load balancing is working by repeatedly querying the load balancer's IP and observing the header alternate between servers:
```bash
curl -sI <lb-01_IP> | grep X-Served-By
```

## Author

Baziwe Trevor Zack
