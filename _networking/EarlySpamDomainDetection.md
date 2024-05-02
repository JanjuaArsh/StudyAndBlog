---
layout: post
title:  "SPF"
date:   2024-04-11
order: 8
---
# Early spam domain detection 

>ref:  "Early Detection of Spam Domains with Passive DNS and SPF"

Spam domains are sources of unsolicited mails and one of
the primary vehicles for fraud and malicious activities such as phishing
campaigns or malware distribution.

# Sender Policy Framework (SPF)
The Sender Policy Framework (SPF) is a protocol used to prevent domain
(mail) spoofing.
SPF is a set of text-form rules in TXT DNS resource records specifying a list of servers
allowed to send mails on behalf of a specific domain. During mail delivery over
the SMTP protocol, the recipient server authenticates the sender Mail Transfer Agent (MTA) by comparing the given MAIL FROM (or HELO) identity and the
sender IP address with the content of the published SPF record.
> A valid SPF version 1 record string must begin with v=spf1 followed by other
SPF entries with the following structure: <qualifier><mechanism>[:<target>].
The most
common SFP mechanisms are the following:
- ip4, ip6 – the sender IP address matches the predefined IP address or the
subnetwork prefix,
- a, mx – the domain has an A (or MX) record that resolves to the sender IP address,
- ptr – a verified reverse DNS query on the sender IP address matches the sending
- domain (not recommended by RFC 7208 [17] since April 2014),
- exists – the domain has an A record,
- include – use the rules of another domain,
- all – the default mechanism that always matches.

Example: b.com IN TXT “include:a.org +ip4:192.0.2.1”