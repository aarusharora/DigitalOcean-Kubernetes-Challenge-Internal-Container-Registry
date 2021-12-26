# DigitalOcean-Kubernetes-Challenge-Internal-Container-Registry

Thank you to DigitalOcean for organizing this challenge. I learnt a lot about Kubernetes while completing this challenge. I had no idea about how K8s worked before but now I know something about it, so great start! I have shared some resources which helped me to get started with kubernetes at the end of this file. BTW, k8s is the new cool way of saying Kubernetes :wink:

## Deploying Harbor on Kubernetes (Easy way for Beginners) - 

+ Setup Kubernetes Cluster on DigitalOcean using their Website - 
  - Login to DigitalOcean Cloud, Choose Kubernetes Option from the side menu.
  - ![Screenshot_20211226_131843](https://user-images.githubusercontent.com/39295812/147416760-358fd064-597a-405d-8082-bb96a33f2168.png)
  - Create cluster with your desired configuration.
  - ![Screenshot_20211226_132030](https://user-images.githubusercontent.com/39295812/147416785-d637117f-3d1a-4203-891e-06ca962181bd.png)
    - I chose the $40/month node plan because Harbor has a hardware pre-requisite -[https://goharbor.io/docs/1.10/install-config/installation-prereqs/]. Don't worry we will destroy the nodes when we are done with our deployment.
  - Follow the instructions to download the configuration file using the doctl cli tool. This will add the cluster configuration to the default namespace (beginner friendly).
  - ![Screenshot_20211226_132521](https://user-images.githubusercontent.com/39295812/147416907-1d3720cb-abbe-432e-8f36-5a39c31bedae.png)
    - It might take some time for the cluster to launch. 
  - Confirm that you can connect to your cluster with kubectl cluster-info
    - If you get this error, it means the cluster has not completely launched yet. 
        - ![Screenshot_20211226_133006](https://user-images.githubusercontent.com/39295812/147417149-5f7fdb00-1f28-4496-8528-195c0c9957ae.png)
    - Successful output looks like this - 
        - ![Screenshot_20211226_133812](https://user-images.githubusercontent.com/39295812/147417205-d001ea79-3a45-418f-8793-930836f8b653.png)
+ Install Helm by following the instructions here - [https://helm.sh/docs/intro/install/]
+ Install Bitnami harbor chart in your cluster [Beginner friendly way to install harbor without worrying about other stuff] - [https://bitnami.com/stack/harbor/helm]. This is the easiest way to setup harbor. It automatically installs the Postgresql database, Redis cluster and the ingress controller required by harbor.
  - ![Screenshot_20211226_135537](https://user-images.githubusercontent.com/39295812/147417501-55dbc371-d803-4c99-8217-a708de30c299.png)
+ Get the load balancer ip using the given command and look at the external ip column of the service with type LoadBalancer.
  - ![Screenshot_20211226_140557](https://user-images.githubusercontent.com/39295812/147417695-4b39b53e-77c0-4a97-ba9b-3497dfcccfab.png)
+ Open the url in browser and viola, Harbor is up and running! We can login using the username 'admin' and the password given above.
  - ![Screenshot_20211226_140747](https://user-images.githubusercontent.com/39295812/147417734-60b631a8-09e6-4c97-982b-e22208b5a2ee.png)
  - ![Screenshot_20211226_140853](https://user-images.githubusercontent.com/39295812/147417760-e810f74b-7311-4165-bd0c-60d332ccea4a.png)
+ Congrats, you did it!

### [Next Steps]
+ Setup Harbor manually by following this guide - [https://goharbor.io/docs/2.4.0/install-config/harbor-ha-helm/]. 
    - I initially tried to setup Harbor by following the instructions in this guide but I was getting CrashLoopBackOff errors and given my limited understanding, I did not know how to troubleshoot the errors so I skipped this guide. But I will try to deploy Harbor with this method in the future. 

### [Resources]
+ DigitalOcean/Kim's Getting started with K8s video - [https://www.digitalocean.com/community/tech_talks/getting-started-with-kubernetes-on-digitalocean]
+ That DevOps Guy's playlist of K8s - [https://www.youtube.com/playlist?list=PLHq1uqvAteVvUEdqaBeMK2awVThNujwMd]
+ DigitalOcean/Fred's video about Containers and K8s - [https://www.youtube.com/watch?v=7WOgYfZgSf0]

### License - MIT
