Project SilentBridge

A dual-layer VPN gateway built by running WireGuard and OpenVPN side-by-side on a single machine.
The goal is to build a fast, resilient, and stealth-capable secure communication system while learning modern VPN architecture and routing.

Overview

Project SilentBridge transforms a standard Linux host into a functional Private Network Gateway that supports:

A WireGuard server running on 10.10.0.0/24

An OpenVPN server running on 10.8.0.0/24

Complete routing separation between both VPNs

NAT forwarding for internet access

Stealth tunneling for OpenVPN using TCP/443

A lightweight, high-speed WireGuard deployment

This repository documents the full configuration, setup steps, and network architecture.

Features

Full WireGuard server setup

WireGuard client configuration template

OpenVPN + Easy-RSA PKI setup

NAT routing and firewall configuration

IPv4 forwarding and system preparation

Step-by-step command explanations

Gateway behavior verification using system utilities

Architecture Summary
WireGuard

Subnet: 10.10.0.0/24

Internal server IP: 10.10.0.1/24

Port: 51820/udp

Identity via public/private key pairs

Minimal overhead and high performance

OpenVPN

Subnet: 10.8.0.0/24

Port: 443/tcp for stealth traffic

PKI-based authentication with Easy-RSA

Uses tun0 virtual interface

Routing

Both VPNs use isolated subnets to avoid route conflicts

NAT ensures external internet access for clients

UFW firewall manages clean port separation (51820/udp & 443/tcp)

The host becomes a full VPN router with IPv4 forwarding enabled


Project_SilentBridge/
│
├── Project SilentBridge.odt          # Full project documentation
├── Project_Silent_Bridge.drawio      # Network architecture diagram
├── README.md                         # Main project overview (this file)
│
├── wireguard/
│   ├── wg0-example.conf              # Example WireGuard server config
│   └── client-template.conf          # Client configuration template
│
└── openvpn/
    ├── server.conf                   # OpenVPN server configuration example  
    ├── EasyRSA-steps.md              # Certificate authority walkthrough
    └── nat-rules.md                  # NAT and firewall documentation

    
System Requirements

Linux host (recommended: Kali Linux, Debian, or Ubuntu)

Root privileges

OpenVPN + Easy-RSA

WireGuard + wireguard-tools

UFW firewall (optional but recommended)
