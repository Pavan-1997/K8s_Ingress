# K8s Ingress

In Kubernetes, an Ingress is an object that allows access to Kubernetes services from outside the Kubernetes cluster. You can configure access by creating a collection of rules that define which inbound connections reach which services.

A Kubernetes Ingress is a robust way to expose Kubernetes services outside the cluster. It lets you consolidate your routing rules to a single resource, and gives a powerful options for configuring these rules, by allowing an API Gateway style of traffic routing.

An Ingress can be configured to give Services externally-reachable URLs, load balance traffic, terminate SSL/TLS, and offer name-based virtual hosting. Ingress lets you configure an HTTP load balancer for applications running on Kubernetes, represented by one or more Kubernetes internal Services.

An Ingress controller is responsible for fulfilling the Ingress, usually with a load balancer, though it may also configure your edge router or additional frontends to help handle the traffic.

The Ingress spec has all the information needed to configure a load balancer or proxy server. It contains a list of rules matched against all incoming requests. Ingress provides routing rules to manage external users’ access to the services in a Kubernetes cluster, typically via HTTPS/HTTP. With Ingress, you can easily set up rules for routing traffic without creating a bunch of Load Balancers or exposing each service on the node. This makes it the best option to use in production environments.

Ingress controllers:

- Ingress controller is an application that runs in a cluster and configures an HTTP load balancer according to Ingress resources. The load balancer can be a software load balancer running in the cluster or a hardware or cloud load balancer running externally. Different load balancers require different Ingress controller implementations.
- In order to Ingress resource work, the cluster must have an ingress controller running.
- You can deploy any number of ingress controllers within a cluster.
- There are many different Ingress controllers, and there’s support for cloud-native load balancers (from GCP, AWS, and Azure).
e.g. Nginx, Ambassador, EnRoute, HAProxy, AWS ALB, AKS Application Gateway

To be noted:

- Ingress is an API object that manages external access to the services in a cluster, typically HTTP. It means you can use Ingress to make your Service accessible from outside.
- Ingress is not a Service type, but it acts as the entry point for the cluster.
- Ingress offers a simplistic gateway type solutions.
- Ingress lets you consolidate your routing rules into a single resource and expose multiple services under the same IP address, using the same load balancers.
- Ingress also enables configuration of resilience (time-outs, rate limiting), content-based routing, authentication and much more.

Use cases:

- Externally reachable URLs for applications deployed in Kubernetes clusters.
- Load balancing rules and traffic, as well as TLS/SSL termination for each hostname, such as foo.example.com.
- Content-based routing:
  - Host-based routing. For example, routing requests with the host header foo.example.com to one group of services and the host header bar.example.com to another group.
  - Path-based routing. For example, routing requests with the URI that starts with /serviceA to service A and requests with the URI that starts with /serviceB to service B.

---

# Creating Ingress - Nginx for Host-based and Path-based routing in Minikube

1. Create the Kubernetes cluster using Minikube 

Follow the Minikube Instructions in OneNote 


2. Clone the repo for manifest files


3. Enable Ingress on Minikube

```
minikube addons enable ingress 
```

4. Now deploy all the manifest files in the repo 
```
kubectl apply -f .
```

5. To view the information about the pods running in a Kubernetes cluster, including additional details such as node name and IP address. 
```
kubectl get pods -o wide
```

6. Since we don't actually have a domain name we can the OS behavious by changing the /etc/hosts file and adding the below

Make sure your on sudo 
```
<IP-Address> foo.bar.com
```

7. Check the domain name by pinging
```
ping foo.bar.com
```

8. Access the application locally 
```
curl -l http://foo.bar.com/bar -v
```


