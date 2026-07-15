# ALU System Engineering & DevOps: Web Server

## Description

This project covers the fundamentals of web servers, HTTP, and DNS. It walks through installing and configuring Nginx on an Ubuntu machine, automating that configuration entirely through Bash scripts (no manual server editing), setting up URL redirection, custom error pages, and registering a real domain name with DNS records pointing to a live server.

## Learning Objectives

By the end of this project, I am able to explain:

- The main role of a web server
- What a child process is
- Why web servers usually have a parent process and child processes
- The main HTTP request methods (GET, POST, etc.)
- What DNS stands for and its main role
- DNS record types: A, CNAME, TXT, MX

## Requirements

- All scripts interpreted on Ubuntu 16.04 LTS
- Every file ends with a new line
- Every Bash script starts with `#!/usr/bin/env bash`
- The second line of every script is a comment explaining what it does
- All scripts pass Shellcheck (v0.3.7) with no errors
- All scripts are executable
- `systemctl` is never used for restarting processes — `service` is used instead

## Directory: `web_server`

| File | Description |
|---|---|
| `0-transfer_file` | Transfers a file to a remote server via `scp`, given a file path, IP, username, and SSH key |
| `1-install_nginx_web_server` | Installs and starts Nginx, serving a page containing "Holberton School" |
| `2-setup_a_domain_name` | Contains the registered `.tech` domain pointing to the web server |
| `3-redirection` | Configures Nginx so `/redirect_me` returns a 301 redirect |
| `4-not_found_page_404` | Configures a custom 404 error page with a specific message |
| `5-design_a_beautiful_404_page.html` | A custom-designed 404 error page |

## Usage

```bash
./0-transfer_file <path_to_file> <server_ip> <username> <path_to_ssh_key>
./1-install_nginx_web_server
./3-redirection
./4-not_found_page_404
```

## Author

Baziwe Zack Trevor
