Heapster Overview
===================

Heapster is a monitoring metrics and events processing tool designed to work inside Kubernetes clusters. It consists of 2 components:

* Heapster core that reads [metrics](model.md) from Kubernetes cluster nodes (see [sources](model.md)),
do some processing and writes them to permanent storage (see [sinks](model.md)).
It also provides metrics for other Kubernetes components through [Model API](model.md).

* Eventer that reads events from Kubernetes master (see [sources](source-configuration.md)) and writes them to permanent storage
(see [sinks](model.md)).
