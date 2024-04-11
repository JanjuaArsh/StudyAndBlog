---
layout: post
title:  "SSH"
date:   2024-04-11
order: 5
---

# Secure Socket Shell (SSH)
***

## Secure Socket Shell (SSH)
It is a cryptographic protocol, primarily used to enable secure access to remote servers and devices over the internet.
It operates on public key cryptography that provides a mechanism for mutual authentication between the server and the client and establishes an encrypted channel of communication between them over an unsecured network.

>> Via SSH, you can remotely connect to CentOS, Debian, Ubuntu and FreeBSD servers. You can connect to a Windows server using the RDP protoco

## SSH is widely used to enable the following functions:
- Secure access to remote systems 
- Secure execution of commands on remote systems
- Secure remote delivery of software updates 
- Secure interactive and automated file transfers
- Auto-login to servers
- Secure management of critical network infrastructure systems such as routers, firewalls, servers, virtual machines, operating systems and more. 

## What are SSH Keys?
SSH keys are a pair of public and private keys that are used to authenticate and establish an encrypted communication channel between a client and a remote machine over the internet.

## How to connect to a Linux server through SSH
The primary way to connect to a Linux server is through SSH protocol. This type of connection is secure, because all the data transferred through it is encrypted.
In order to establish an SSH connection you should configure it on the remote server that you want to connect to, and the client on the user’s side. 
As a rule, the OpenSSH client is installed on Linux by default and does not require additional manual configuration. Connection can be established from the terminal with the help of ssh command. Parameters in this case would be username and IP address of the remote server.

## Working of ssh
The client and server establish a secure ssh communication channel.
-Client-side component. A client-side component is an application or program used to connect to another machine. The client uses remote host information to initiate the connection through the program. If the credentials are verified, the program establishes an encrypted connection.
- Server-side component. On the server's side, an SSH daemon constantly listens to a specific TCP/IP port (the default SSH port number is 22) for possible client connection requests. Once a client initiates a connection through the defined port, the SSH daemon responds with the software and the protocol versions it supports. The default protocol version for SSH communication is version 2.
- Key exchange. The client and server exchange cryptographic keys to create a secure communication channel. The keys help encrypt subsequent communication.
- Authentication. When establishing a connection, the client provides identification data to the server (as a username/password or SSH keys). If the provided credentials are correct, SSH creates a new encrypted communication session.



