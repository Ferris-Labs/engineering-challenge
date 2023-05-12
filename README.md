# ferris labs - engineering-challenge

### How would you solve the following engineering challenge?

## Context & Background

The ferrisDX platform consists of the following technical FOSS components engineered to work as an
**event-based micro-services integration platform** on top of any Kubernetes or dedicated compute
infrastructure. It is designed to be **cloud native** and abstracted away from hyperscaler propietary
services.

* ArgoCD
* Consul
* Kafka
* Minio
* PostGreSQL
* Vault
* Keycloak
* Elastic
* Flask

As optional components depending on the use case of the clients the following application level containers
can be added to the platform - either by being deployed alongside in the ferris K8S namespace or by utilzing
existing client implementations:

* Theia based IDEs
* JupyterHub Notebook Server
* Presto or Trino SQL abstraction layers
* any DB flavor (RDBMS, DocDBs, GraphDBs, other)

It utilises the following set of open standards throughout the components and every addition or change
needs to adhere to these standards or impose an additional (equally open and universal) standard that
does not confilct with the existing ones.

* OpenAPI - REST and Async (for all services)
* Cloud Events (for all event wrappings)
* S3 (for any file abstraction)
* JDBC / SQLAlchemy for any DB abstraction

## Challenge Objective

We want to introduce a more genralistic and universal approach to *Metadata Handling*. At the moment all
metadata is stored in __PostGres__ or in specific text-files (.YAML or .JSON) in order to be useful for both
code and human readability.

### Design Goal

Think of an approach that works for the following three use cases in a similar fashion and produces the same
or comparable results for all three use cases. Design the *Metadata Handling* for the following components:

1. a REST API layer that offers FCRUD endpoints for an Oracle business database (32 endpoints)
1. a set of event producers and consumers that create an event flow upon a web-user click-journey (3 topics
and 8 different event types / schemas)
1. a file-handling service that scrapes target URLs for distinct file-types and puts the results on Minio/S3
(resulting in 300-500 new files per day across 5 different buckets)

Remember that you can utilize all of the components in play on the ferrisDX platform already and that you do
NOT have to reinvent the wheel.

## Requirements

The new component to be designed needs to:
* work for GDPR (PII) / data security, data cataloging, and data quality aspects of metadata
* be deployable as a Python library (pip install) or as a K8S pod / container via ArgoCD
* have its independent lifecycle with minimum (hard) dependencies on other components
* establish a *Metadata Standard* to be used across the three use cases as stated above
* also serve as a template for any (similar) client implemented use case (with either API, event or file pattern)

The new component can:
* use an existing metadata standard (if it fits the picture and is extensible)
* extend an existing standard
* define a new skeleton for the currently known aspects

## Challenge Response

At a minimum write your response as **response.md** to this repository. You additionally can:
* cross-reference any links to documentation / standards / components you would use / apply
* include schematics for how you would envision such a metadata handling to work
* include a rough breakdown of which elements you would deliver when along 2 week sprints
* use our second interview as an opportunity to discuss and clarify any questions

Please commit and push your response at your convenience within the next 7 business days and
drop us a quick mail at [tom@ferrislabs.net](mailto://tom@ferrislabs.net) as soon as you have pushed.

