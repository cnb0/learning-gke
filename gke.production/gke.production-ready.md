# Preparing a Google Kubernetes Engine environment for production

```
 - Structuring projects, Virtual Private Cloud (VPC) networks, and clusters
        - GCP Projects
        - Clusters
        - Networks and subnets
        - Multi-zone and regional clusters
             - Multi-zone clusters:
                 - Create a single cluster master in one zone.
                 - Create nodes in multiple zones.
             - Regional clusters:
                 - Create three cluster masters across three zones.
                 - By default, create nodes in three zones, or in as many zones as you want.
            - The primary difference between regional and multi-zone clusters is that 
            regional clusters create three masters and multi-zone clusters create only one

            - You can choose to create multi-zone or regional clusters at the time of cluster creation. 
            - You can add new zones to an existing cluster to make it multi-zone. 
            - you cannot modify an existing cluster to be regional. 
            - You also cannot make a regional cluster non-regional.

        - Master authorized networks
        - Private clusters
            - By default, all nodes in a GKE cluster have public IP addresses

- Managing identity and access
        - Project-level access
        - Role-based access control (RBAC)
        - Image access and sharing
            - Making images public in Container Registry
            - Accessing images across projects in Container Registry
            - Determining the right image pull policy
            - Using dynamic admission webhooks to enforce policies

- Using Workload Identity to interact with Google Cloud service APIs
        - Managing cluster security
        - Vulnerability scanning for images
        - Binary Authorization
        - Secure access with gVisor in GKE Sandbox
        - Audit logging
                - Examples of what you might want to check and alert on are the following:
                        - Deleting a deployment.
                        - Attaching to or using exec to access a container that has privileged access.
                        - Modifying ClusterRole objects or creating role bindings for the cluster roles.
                        - Creating service accounts in the kube-system namespace.
        - PodSecurityPolicies
        - Container security considerations
                - The fundamental building block for Kubernetes services is the container. 
                - This makes container security a key factor when you plan cluster security and policies. 
                  Carefully consider the following:
                      -  The images that you build your containers from.
                      -  The privileges that you assign to containers.
                      -  How containers interact with the host OS and other services.
                      -  How containers access and log sensitive information.
                      -  How you manage the lifecycle of the containers in your clusters.

- Configuring networking
          - VPC-native clusters compared to routes-based clusters
          - Communicating within the same cluster
                - Service discovery
                - DNS
                - Packet flow: ClusterIP
                - Headless services
                - Network policies
          - Connecting to a GKE cluster from inside Google Cloud
          - Connecting from inside a cluster to external services
                - Stub domains
                - External name services
                - Services without selectors
          - Configuring your services in Kubernetes to receive internet traffic
                - Backend configuration
                    - You can supplement the configuration of the load balancer with specifications like the following:
                       - Enabling caching with Cloud CDN.
                       - Adding IP address or CIDR allowlists (whitelists) with Google Cloud Armor.
                       - Controlling application-level access with Identity-Aware Proxy (IAP).
                       - Configuring service timeouts and connection-draining timeouts for services that are
                         governed by the Ingress   object in a cluster.
                 - Using a service mesh
                        - A service mesh provides a uniform way to connect, secure, and manage microservices
                           that are running in your Kubernetes clusters
                        - Key features that a service mesh provides are the following:

                            - Traffic management. 
                               - The service mesh allows you to define granular rules that 
                                 determine how traffic should be routed and split among services or among 
                                 different versions of the same service. This makes it easier to 
                                 roll out canary and blue-green deployments.

                            - Built-in observability. 
                              - The mesh records network traffic (Layer 4 and Layer 7)
                                metrics in a uniform manner without requiring you to write 
                                code to instrument your services.

                            - Security. 
                               - The mesh enables mutual TLS (mTLS) between services.
                                 It not only provides secure channels for data in transit but
                                 also helps you manage the authentication and authorization of services 
                                 within the mesh.
                - Firewalling
                - Connecting to an on-premises data center


 - Managing cluster operability       
        - key factors to consider when you're administrating and operating your GKE clusters
            - Resource quotas
            - Resource limits
            - Pod disruption budgets
            - Managing Kubernetes upgrades
            - Upgrading the Kubernetes version
            - Node auto-repair
            - Autoscaling GKE clusters
                - Cluster autoscaler
                - Horizontal Pod Autoscaling (HPA)
                - Vertical Pod Autoscaling (VPA)
                - Node auto-provisioning



```