# GCP Outline

## Structure

* GCP is intrinsincally global
* One or more datacenters are in **zones**
* Zones are grouped in **regions**
* Regions are grouped in **multi-regions**
* Multi-regions are connected in a private global network (fiber). Traffic from server to server don't touch the internet
* Points of Presence (POPs) - Network edges and CDN Locations

## Pricing

* Provisioned - prepaid
* Usage - elastic
* Network Traffic
    * Free ingress
    * Egress is sometimes free, depends on services and location

## Security

* Everything is encrypted at rest
* Network encryption
    * All control info is encrypted
    * All WAN traffic is going to be encrypted automatically
    * Moving towards encrypting all local traffic within data centers

## Scale and Automation

* Infinate scaling
* Automate everything
* Resource Quotas (soft limits set by google)
    * Query for resource limits: `gcloud compute project-info describe --project <project-id>`

## Organization

* Projects are top level and are similar to AWS accounts

