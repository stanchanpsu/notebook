# Compute

## Compute Engine (GCE)

* Zonal
* Virtual Machines
* Can customize exact CPU count and RAM
* pay by second (60 second min.)
* **Sustained Use Discount** - automatically cheaper the longer you run (like AWS reserve)
* Preemptible instances can be turned off whenever (like AWS Spot)

## Kubernetes Engine (GKE)

* Managed Kube cluster
* No IAM integration
* Integrates with Persistent Disk for storage
* Pay for underlying GCE instances
    * No GKE management fee, no matter cluster size

## App Engine (GAE)

* PaaS to take code and run it (like Beanstalk or Heroku)
* Flex mode (App Engine Flex) can run any container
* Autoscales based on load

## Cloud Functions (GCF)

* FaaS, only runs NodeJS or other languages with "shims"
* Automatically gets an HTTP endpoint. Can be triggered without a gateway