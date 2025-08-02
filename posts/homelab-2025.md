---
author: "Alecks"
title: "State of my Homelab in 2025"
date: "2025-08-02"
description: "yearly check in on how my homelab setup is going."
slug: homelab-2025
---

Fully moving off the cloud has been a bigger task than I anticipated, however its been an incredibly fun and rewarding journey. It's taught me tons about security, networking, computer hardware, virtualisation and more.

Obviously I still depend on cloud hosted services like cloudflare (dns), proton (email, drive) but I don't operate any of my own servers up there.

This setup hosts umami, pyrodactyl panel, game servers, websites for friends and of course this website.

## Hardware Setup
Everything is second hand off ebay or from family/friends for a few reasons
 - Great value for money and super cheap
 - Helps reduce ewaste (giving these machines a new life)

even with older specs they easily fit my needs. my current compute nodes include: 

| Name | CPU | Memory | Storage | Price | 
|----------|----------|----------|----------|----------|
| Railway  | i5-7400T  | 8GB DDR4  | 256GB NVMe SSD  | $100 AUD |
| Freight  | i7-4770  | 16GB DDR3 | 500GB SATA SSD     | $150 AUD | 


## Software Setup
Both bare metal machines run Proxmox VE clustered together. VMs run a mix of Ubuntu 24.04 and Debian 12.02.

All services run in docker for convenience and portability. 

## Security & Remote Access
Only public services are port forwarded and tailscale is used to access internal services from outside my lan.

Many security measures are in place on internal machines like firewalls, ssh keys / ssh login notifications (to ntfy), fail2ban and more.

## Networking Setup

Since only one ip address is availale, I run a debian lxc container with caddy which listens on port 80/443 and forwards web traffic to internal servers.

For the uplink, I have a gigabit plan from Launtel who I've been using for 2 years and never had a single issue with.

| Launtel Service Inclusions |
|----------|
| GSL DDoS Protection |
| Support and allow self-hosting on their network |
| Static ip for a $100 deposit (Refundable whenever)

## Internal and External Monitoring
I'm currently not running a local monitoring service but I use HetrixTools heartbeat agents to monitor server resources and status combined with ntfy hosted on a gcp free tier instance for push notifications about incidents.

## Server Backups
A backup system isn't in place yet but whenever I get round to it servers will be backed up to Backblaze or some other backup service and a local backup server.

## Wrapping up
Some things I plan to do in the future include:
- Buy a new router or build one myself (pfsense) for vlan support to properly segment my network and mitigate the risk of a server being compromised and attacking stuff on my lan.

- Remote cloud desktop service with another mini pc, for remote development or just general use using apache guacamole and xrdp.

- Dedicated shared vm for friends to run their stuff on instead of using my vms.

- Develop a proper backup strategy.

Thats all from me, I plan to get back into blogging over these next few months so expect some new content here. Adios.