# Networking

## Google Domains (Route53)

* Global
* Google's registrar for Domain Names
* Private Whois records
* Built-in DNS or custom nameservers
* Supports DNSSEC
* Email forwarding with automatic setup of SPF and DKIM (built in DNS)

## Cloud DNS

* Scalable, reliable & managed authoritative Domain Name System (DNS) service
* 100% uptime guarentee
* low latency globally
* supports DNSSEC
* pay fixed fee per hosted zone to store and distribute DNS
    * pay for DNS lookups

## Static IP (AWS Elastic IP)

* Regional or Globa
* reserve static IP addresses in projects and assign them to different resources
* regional IPs used for GCE instances & network load balancers
* gloabl IPs used for global load balancers: HTTP(S), SSL proxy & TCP proxy
    * Anycast IP - simplifies DNS
* Pay for reserved IPS not in use

## Load Balancing

* high perf, scalable traffic distribution integrated with autoscaling & cloud CDN
* SDN naturally handles spikes without any prewarming; no instances or devices
* Regional Network Load Balancer: health checks, round robin, session affinity
    * forwarding rules based on IP, protocol (TCP, UDP) and optionally port
* Global Load Balancer: multi-region failover for HTTP(S), SSL proxy, & TCP (proxy)
    * prioritize low-latency connection to region near user, with failover
    * reacts quickly, unlike DNS, to change in users, traffic, network, health, etc...
* Pay by making ingress traffic billable (cheaper for egress) plus hourly per rul

## Cloud CDN (AWS Cloudfront)

* low latency content delivery based HTTPS(S) clb & integrated with GCE & GCS
* supports HTTP/2 and HTTPS, but no custom origins (GCP only)
* Simple checkbox on HTTPS(S) load balancer turns it on
* When a user requests data that isn't at a cache site already, a cache fill request results in network egress charges from origin to point-of-presence and then cached
* always pay point-of-presence to client egress charges
* pay for HTTP(S) request volume
* pay for cache invalidation request (not per resource invalidated)
* origin costs (CLB, GCS) can be much lower with good caching strategy

## Virtual Private Cloud (VPC)

* global IPv4 unicast software-defined network (SDN) for GCP resource
* automatic mode is easy, custom mode gives control
* configure subnets (each with private IP range), routes, firewalls, VPNs, BCP, etc
* VPC is global and subnets are regional (not zonal)
    * GCE across a region under one VPC
* can be shared across multiple projects in same org and peered with other VPCs
* can enable private (internal IP) access to some GCP services (eg. BQ, GCS)
* Free to configure
* pay to use services for network egress

## Cloud Interconnect

* options for connecting external networks to google's network
* private connections to VPC via Cloud VPN or dedicated interconnect (with SLAs)
* public Google services (including GCP) accessible via external peering (no SLAs)
    * direct peering for high volume
    * carrier peering via a partner for low volume
* significantly lower egress fees
    * except cloud VPN which stays the same

## Cloud Virtual Private Network (VPN)

* IPsec VPN to connect to VPC via public internet for low-volume data connections
* for persistent, static connections between gateways
    * peer VPN gateway must have static IP
* encrypted link to VPC (as opposed to dedicated interconnect) into one subnet
* supports both static and dynamic routing
* 99.9% availability
* pay per tunnle-hour

## Dedicated Interconnect (AWS Direct Connect)

* Direct physical link between VPC and on-prem for high volume data connections
* VLAN attachment is private connection to VPC in one region; no public GCP APIs
    * region chose from those supported by particular interconnect location
* links are private but not encrypted, can layer on own encryption
* redundant connections in different locations recommended for critical apps
    * redundancy achieves 4 9s availability; otherwise 3 9s
* pay for 10 Gbps link plus smaller fee for VLAN attachment
* pay reduced egress rates from VPC that go through the interconnect

## Cloud Router

* Dynamic routing for hybrid networks linking GCP VPCs to external networks
* works with Cloud VPN and dedicated interconnect
* automatically learns subnets in VPC and announces them to on-prem network
* without cloud router you must manage static routes for VPN
    * changing IP addresses on either side of VPN requires recreating it
* Free to set up
* pay for usual VPC egress charges

## CDN Interconnect

* direct low latency connectivity to certain external CDN providers with cheaper egress
* works for both pull and push cache fills
* contact CDN provider to set up for GCP project and which regions