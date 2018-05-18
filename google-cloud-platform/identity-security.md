# Identity and Security

## Roles (AWS Policies)

* Roles are collections of Permissions to use or manage GCP resources
* Permissions allow you to perform certain actions: `Service.Resource.Verb`
* Primitive Roles: Owner, Editor, Viewer
    * viewer - read only
    * editor - change things
    * owner - control access & billing
    * pre-date IAM service, may still be useful, but often too broad
* Predefined Roles: Give granular access to specific GCP resources
* Custom Roles: project or Org-level collections you define of granular permissions

## Cloud IAM

* Controls access to GCP resources: authorization, not really authentication/identity (like AWS IAM)
* Member is user, group, domain, service account, or the public
    * Individual Google account, Google group, G Suit/Cloud identity domain
    * Service Account - belongs to application/instance not individual user
    * every identity has a unique email address, even service accounts
* Policies bind Members to Roles at a hierarchy level: Org, Folder, Project, Resource
    * who can do what to which things
* IAM is free

## Service Accounts

* type of google account that represents an application, not an end user
* can be assumed by applications or individual users (when so authorized)
* for almost all cases, use service accounts rather than user accounts or API keys
* consider resources and permissions required by application; use least privilege
* can generate and download private keys (user managed keys), for non GCP, but
* Cloud Platformed managed keys are better for GCP.
    * No direct downloading: google manages private keys and rotates them once a day

## Cloud Identity

* Identity as a Service to provision and manage users and gorups
* Free Google Accounts for non-G-Suite users, ited to a verified domain
* Centrally manage all users in Google Admin console; supports compliance
* 2-step verification and enforcement, including keys
* Sync from active directory and LDAP directories via Google Cloud Directory sync
* Identities work with other google services
* identities can be used to SSO with other apps via OIDC, SAML, OAUTH2
* Free to use

## Security Key Enforcement

* USB or Bluetooth 2-step verification device that prevents phishing
* device verifies target service
* eliminates man-in-the-middle attack

## Cloud Resource Manager

* Centrally manage & secure organization's projects with custom folder hierarchy
* Organization resource is root node in hierarchy; folders per business needs
* tied 1:1 to a cloud identity / G suit domain, then owns all newly created projects
    * without this organization, specific identities (people) must own GCP projects
* recycle bin - allows undeleting projects
* define custom IAM roles at org level
* apply IAM policies at organization, folder, or project level

## Cloud Audit Logging

* Who did what/where/when (like CloudTrail)
* Maintains two audit logs for each project and organization:
    * Admin Activity (400 day retention, free)
    * Data Access (7 day retention; 30 day retention paid)
        * for GCP visible services
* Stackdriver-family service

## Cloud KMS

* Low-latency service to manage & use AES256 encryption keys to protect secrets
* move secrets out of code and into the environment, in a secure way
* integrated with IAM & Cloud Audit logging to authorize & track key usage
* rotate keys used for new encryption either automatically or on demand
    * still keeps old active key versions to allow decrypting
* key deletion has 24 hour delay; to prevent malicious data loss or accidental
* pay for active key versions stored over time
* pay for key use operations (encrypt/decrpt; admin operations are free)

## Cloud Identity-Aware Proxy (IAP)

* Guards apps running on GCP through identity verification instead of VPN Access
* Based on cloud load balancer & IAM, and only passes authed requests through
* grant access to any IAM identities, including groups & service accounts
* Grant access to any IAM identities, including gorups & service accounts
* relatively straightforward to set up
* pay for load balancing/protocol forwarding rules and traffic

## Cloud Security Scanner

* Free but limited GAE app vulnerability scanner with "Very low false positive rates"
* can identify
    * XSS
    * Flash injection
    * Mixed content
    * outdated/insecure libraries

## Cloud Data Loss Prevention API (DLP)

* Finds and optionally redacts sensitive info in unstructured data streams
* helps you minimize what you collect expose or copy to other systems
* data can be sent directly or API can be pointed at GCS, BQ, or Cloud Datastore
* can scan both text and images
* pay for volume of data processed (priced per GB)