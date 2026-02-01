**AWS Web Hosting Foundations**

Overview
---


This project implements a foundational web hosting architecture designed to mirror real-world infrastructure patterns. Rather than focusing on advanced services or abstractions, the goal was to validate the underlying systems required to make an internet-facing resource reachable, controlled, and reliable.

The architecture emphasizes network boundaries, access control, and availability, implemented using AWS to reflect how these concepts translate in a cloud environment.


Architecture Summary
---


The environment is built around a custom VPC with public and private subnets. Internet-facing traffic is terminated at an Application Load Balancer, while web servers remain isolated within private subnets. Administrative access is handled through a bastion host to avoid direct public exposure.


Key components:

---

* VPC with public and private subnets
* Internet Gateway and NAT Gateway
* Bastion host for controlled SSH access
* EC2 instances hosting the web application
* Application Load Balancer for traffic distribution
* Auto Scaling Group for availability
* Route 53 and ACM for DNS and HTTPS


Design Perspective
---


This project is intentionally foundational. While the workload itself is simple, the structure reflects patterns commonly used in enterprise environments:


* Public access is limited to the minimum required surface
* Internal resources remain private by default
* Traffic flow is explicit and traceable
* Availability is considered even when not strictly necessary


The focus was less on “getting a site online” and more on validating how systems are layered and protected before applications are even considered.


Security Considerations

---

* Web servers are deployed in private subnets with no direct internet access
* SSH access is restricted through a bastion host
* Security groups are scoped tightly to expected traffic paths
* HTTPS is terminated at the load balancer using ACM-managed certificates
* IAM roles are used to control service-level access


Operational Notes
---


The environment supports horizontal scaling through an Auto Scaling Group

Health checks are handled at the load balancer level

The architecture can be simplified or expanded depending on cost and traffic requirements


Why This Matters
---


Before optimization, automation, or advanced services, systems need a solid foundation. This project reinforces how availability, controlled access, and predictable behavior are established at the infrastructure level -- concepts that apply regardless of platform or scale.

