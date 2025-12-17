# Google Cloud Platform (gcloud) Cheat Sheet

This document serves as a quick reference for common `gcloud` commands, focusing on configuration, compute instances, and infrastructure exploration.

## 1. Configuration Management (`gcloud config`)

Manage your active project, region, zone, and authentication settings.

| Command | Description |
| :--- | :--- |
| `gcloud config list` | Show all properties in your active configuration. |
| `gcloud config configurations list` | List all available named configurations. |
| `gcloud config configurations activate [CONFIGURATION_NAME]` | Activate an existing named configuration. |
| `gcloud config configurations describe [CONFIGURATION_NAME]` | Describe the attributes of a specific configuration. |
| `gcloud config set project [PROJECT_ID]` | Set the project for the current configuration. |

**Example:**
```bash
gcloud config configurations list
gcloud config configurations activate my-default-configuration
gcloud config list
gcloud config configurations describe my-second-configuration
```

## 2. Compute Instances (`gcloud compute instances`)

Create, list, and manage virtual machine instances.

| Command | Description |
| :--- | :--- |
| `gcloud compute instances list` | List all instances in the current project. |
| `gcloud compute instances create [INSTANCE_NAME]` | Create a new instance with default settings. |
| `gcloud compute instances describe [INSTANCE_NAME]` | Display details of a specific instance. |
| `gcloud compute instances delete [INSTANCE_NAME]` | Delete a specific instance. |

**Example:**
```bash
gcloud compute instances list
gcloud compute instances create my-first-instance-from-gcloud
gcloud compute instances describe my-first-instance-from-gcloud
gcloud compute instances delete my-first-instance-from-gcloud
```

## 3. Zones and Regions (`gcloud compute zones/regions`)

Explore available geographic locations for your resources.

| Command | Description |
| :--- | :--- |
| `gcloud compute zones list` | List all available zones. |
| `gcloud compute regions list` | List all available regions. |
| `gcloud compute regions describe [REGION]` | Display details about a specific region. |
| `gcloud compute zones list --filter="region:[REGION]"` | List zones within a specific region. |
| `gcloud compute zones list --sort-by=[FIELD]` | Sort the list of zones by a field (e.g., `region`). |
| `gcloud compute zones list --uri` | List the URIs of all zones. |

**Example:**
```bash
gcloud compute zones list
gcloud compute regions list
gcloud compute regions describe us-west4
gcloud compute zones list --filter=region:us-west2
gcloud compute zones list --sort-by=region
gcloud compute zones list --sort-by=~region
gcloud compute zones list --uri
```

## 4. Machine Types (`gcloud compute machine-types`)

Explore available hardware configurations for your instances.

| Command | Description |
| :--- | :--- |
| `gcloud compute machine-types list` | List all available machine types. |
| `gcloud compute machine-types list --filter="zone:[ZONE]"` | List machine types available in a specific zone. |

**Example:**
```bash
gcloud compute machine-types list
gcloud compute machine-types list --filter zone:asia-southeast2-b
gcloud compute machine-types list --filter "zone:(asia-southeast2-b asia-southeast2-c)"
```

## 5. Instance Templates (`gcloud compute instance-templates`)

Manage templates for creating instances with identical configurations.

| Command | Description |
| :--- | :--- |
| `gcloud compute instance-templates list` | List all instance templates. |
| `gcloud compute instance-templates create [TEMPLATE_NAME]` | Create a new instance template. |
| `gcloud compute instance-templates describe [TEMPLATE_NAME]` | Display details of an instance template. |
| `gcloud compute instance-templates delete [TEMPLATE_NAME]` | Delete an instance template. |

**Example:**
```bash
gcloud compute instance-templates list
gcloud compute instance-templates create instance-template-from-command-line
gcloud compute instance-templates describe my-instance-template-with-custom-image
gcloud compute instance-templates delete instance-template-from-command-line
```

# kubectl cmds
```bash
gcloud config set project my-kubernetes-project-304910
gcloud container clusters get-credentials my-cluster --zone us-central1-c --project my-kubernetes-project-304910
kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl get deployment
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
kubectl get services
kubectl get services --watch
curl 35.184.204.214:8080/hello-world
kubectl scale deployment hello-world-rest-api --replicas=3
gcloud container clusters resize my-cluster --node-pool default-pool --num-nodes=2 --zone=us-central1-c
kubectl autoscale deployment hello-world-rest-api --max=4 --cpu-percent=70
kubectl get hpa
kubectl create configmap hello-world-config --from-literal=RDS_DB_NAME=todos
kubectl get configmap
kubectl describe configmap hello-world-config
kubectl create secret generic hello-world-secrets-1 --from-literal=RDS_PASSWORD=dummytodos
kubectl get secret
kubectl describe secret hello-world-secrets-1
kubectl apply -f deployment.yaml
gcloud container node-pools list --zone=us-central1-c --cluster=my-cluster
kubectl get pods -o wide
 
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get services
kubectl get replicasets
kubectl get pods
kubectl delete pod hello-world-rest-api-58dc9d7fcc-8pv7r
 
kubectl scale deployment hello-world-rest-api --replicas=1
kubectl get replicasets
gcloud projects list
 
kubectl delete service hello-world-rest-api
kubectl delete deployment hello-world-rest-api
gcloud container clusters delete my-cluster --zone us-central1-c
```
## Auth cmds

```bash
gcloud compute project-info describe
gcloud auth list
gcloud projects get-iam-policy glowing-furnace-304608
gcloud projects add-iam-policy-binding glowing-furnace-304608 --member=user:in28minutes@gmail.com --role=roles/storage.objectAdmin
gcloud projects remove-iam-policy-binding glowing-furnace-304608 --member=user:in28minutes@gmail.com --role=roles/storage.objectAdmin
gcloud iam roles describe roles/storage.objectAdmin
gcloud iam roles copy --source=roles/storage.objectAdmin --destination=my.custom.role --dest-project=glowing-furnace-304608
```

## Cloud sql

```bash
# Cloud SQL
gcloud sql connect my-first-cloud-sql-instance --user=root --quiet
gcloud config set project glowing-furnace-304608
gcloud sql connect my-first-cloud-sql-instance --user=root --quiet
use todos
create table user (id integer, username varchar(30) );
describe user;
insert into user values (1, 'Ranga');
select * from user;
 
# Cloud Spanner
CREATE TABLE Users (
  UserId   INT64 NOT NULL,
  UserName  STRING(1024)
) PRIMARY KEY(UserId);
 
 
# Cloud BigTable
bq show bigquery-public-data:samples.shakespeare
 
gcloud --version
cbt listinstances -project=glowing-furnace-304608
echo project = glowing-furnace-304608 > ~/.cbtrc
cat ~/.cbtrc
cbt listinstances
```
## Cloud PubSub

```bash
gcloud config set project glowing-furnace-304608
gcloud pubsub topics create topic-from-gcloud
gcloud pubsub subscriptions create subscription-gcloud-1 --topic=topic-from-gcloud
gcloud pubsub subscriptions create subscription-gcloud-2 --topic=topic-from-gcloud
gcloud pubsub subscriptions pull subscription-gcloud-2
gcloud pubsub subscriptions pull subscription-gcloud-1
gcloud pubsub topics publish topic-from-gcloud --message="My First Message"
gcloud pubsub topics publish topic-from-gcloud --message="My Second Message"
gcloud pubsub topics publish topic-from-gcloud --message="My Third Message"
gcloud pubsub subscriptions pull subscription-gcloud-1 --auto-ack
gcloud pubsub subscriptions pull subscription-gcloud-2 --auto-ack
gcloud pubsub topics list
gcloud pubsub topics delete topic-from-gcloud
gcloud pubsub topics list-subscriptions my-first-topic
```
## Cloud IAC


 * [Terraform Link](https://developer.hashicorp.com/terraform/language/block/resource)

## 6. External Resources

For more comprehensive documentation and advanced usage, refer to these resources:

- **Official Google Cloud SDK Cheat Sheet**: [Reference Guide](https://cloud.google.com/sdk/docs/cheatsheet)
- **Official gcloud compute instances documentation**: [Google Cloud Docs](https://cloud.google.com/sdk/gcloud/reference/compute/instances)
- **Awesome Google Cloud**: A curated list of resources - [GitHub](https://github.com/google/awesome-google-cloud)
- **GCloud Cheat Sheet (Gist)**: Community-contributed cheat sheet - [GitHub Gist](https://gist.github.com/pydevOps/c749d502769910e5d033a36db5285785)
- **GridU Cheat Sheets**: Various GCP cheat sheets - [GitHub](https://github.com/GridU/GCP-Cheat-Sheets)
- **Denny Zhang's GCP Cheat Sheet**: [GitHub](https://github.com/dennyzhang/cheatsheet-gcp-A4)
