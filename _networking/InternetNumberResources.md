---
layout: post
title:  "Internet number resources"
date:   2024-04-07
order: 1
---

# Internet number resources 
***

## IP addresses
IP stands for Internet Protocol, it is a set of rules that defines how computers communiate over a network. Each device on the internet has an IP address assigned to it. An IP is required so that information can be send to and from the device. There are two versions of IP - IPV4 and IPV6. IPV4 is 32 bits and IPV6 is 128 bits. IPv6 uses hexadecimal notation to allow for more combinations.

## Autonomous systems
In (Request for Comments)RFC 1930 BGP-4 states that:
>> "The classic definition of an Autonomous System is a set of routers
 under a single technical administration, using an interior gateway
 protocol and common metrics to route packets within the AS, and
 using an exterior gateway protocol to route packets to other ASes.
 Since this classic definition was developed, it has become common
 for a single AS to use several interior gateway protocols and
 sometimes several sets of metrics within an AS. The use of the
 term Autonomous System here stresses the fact that, even when
 multiple IGPs and metrics are used, the administration of an AS
 appears to other ASes to have a single coherent interior routing
 plan and presents a consistent picture of what networks are
 reachable through it."

To rephrase succinctly:
 An AS is a connected group of one or more IP prefixes run by one
 or more network operators which has a SINGLE and CLEARLY DEFINED
 routing policy.

## Internet Assigned Numbers Authority(IANA)
IANA is responsible for distributing IP addresses and ASNs worldwide. It distributes large blocks to RIRs.

## Regional Internet Registries (RIR)
Globally, there are five Regional Internet Registries, or RIRs. Within their designated regions, RIRs oversee the management, distribution, and registration of Internet number resources, including Autonomous System (AS) Numbers and IPv4 and IPv6 address space.
- (AFRINIC) African Network Coordination Centre
- (APNIC) Asia-Pacific Network Coordination Centre
- (ARIN) American Registry for Internet Numbers
- (LACNIC) Latin American and Caribbean Internet Addresses Registry
- (RIPE NCC) Réseaux IP Européens Network Coordination Centre

The Regional Internet Registries (RIRs) designate ASNs and distribute smaller IP address blocks to the Internet Service Providers (ISPs), National Internet Registries (NIRs), and Local Internet Registries (LIRs) in their respective regions. I

## Routing 
Routing is the transfer of data over the internet. The data from the source can be split into multiple packets, each having the destination address.routers pass packets through the internet by analysing the routing table. The pakets may take different paths and are reassembeled upon arrival at destination.