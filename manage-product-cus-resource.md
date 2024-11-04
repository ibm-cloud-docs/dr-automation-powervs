---
front_matter_title: "Manage product on customer resources"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Manage product on customer resources

Managed products on customer's resources are orchestrated by IBM. They are single-tenant and data plane products. They are accessed locally in customer accounts, data plane hosted on virtual resources in the customer’s account, control plane security owned by IBM, and data plane security owned by the customer. IBM Cloud products of this type include IBM Cloud Kubernetes Service on classic infrastructure and Red Hat® OpenShift® on IBM Cloud® on classic infrastructure.

Table 1. Responsibility Matrix for Managed Products on Customer’s Resources

| Resource                    | Incident and Operations Management | Change Management | Identity and Access Management | Security and Regulation Compliance | Disaster Recovery |
|-----------------------------|------------------------------------|-------------------|--------------------------------|-------------------------------------|--------------------|
| Data                        | Customer                           | Customer          | Customer                       | Customer                            | Customer           |
| Application                 | Customer                           | Customer          | Customer                       | Customer                            | Customer           |
| Service instance            | Shared                             | Shared            | Shared                         | Shared                              | Shared             |
| Operating system            | Shared                             | Shared            | Shared                         | Shared                              | Shared             |
| Virtual and bare metal      | Shared                             | Shared            | Shared                         | Shared                              | Shared             |
| Virtual storage             | Shared                             | Shared            | Shared                         | Shared                              | Shared             |
| Virtual network             | Shared                             | Shared            | Shared                         | Shared                              | Shared             |
| Hypervisor                  | IBM                                | IBM               | IBM                            | IBM                                 | IBM                |
| Physical servers and network| IBM                                | IBM               | IBM                            | IBM                                 | IBM                |
| Physical storage            | IBM                                | IBM               | IBM                            | IBM                                 | IBM                |
| Physical network            | IBM                                | IBM               | IBM                            | IBM                                 | IBM                |
