## Setting up a cloud solution environment

#### Question: What is the easiest way to clone a project?

- [x] There is no general way to automatically clone a project. You must handle each resource separately.
  - _There’s no automatic functionality for this, and Google Support cannot and will not get involved in such an undertaking._

#### Question: You need to start a set of virtual machines to run year-end processing in a new GCP project. How can you enable the Compute API in the fewest number of steps?

- [x] Navigate to the Compute section of the console.
  - _There is no such thing as a “defaults” project. Each API must be enabled before it can be used. Some APIs are enabled by default, but GCE is not. Navigating to the Compute Engine of the console automatically enables the GCE API. You do not have to configure authentication to be able to use Cloud Shell, but regardless, using Cloud Shell would take more steps than simply navigating to the GCE console._

#### Question: Google has just released a new XYZ service and you would like to try it out in your pre-existing Skunkworks project. How can you enable the XYZ API in the fewest number of steps?

- [x] Open Cloud Shell, run **gcloud services enable xyz.googleapis.com**
- [x] Open Cloud Shell, run gcloud services enable xyz
  - _Google does not generally enable new services by default for existing projects. Cloud Shell does not require you to configure authentication. GCP Support does not get involved with things like enabling APIs for you; that's something you simply do for yourself. The gcloud command to enable the service can include googleapis.com._

#### Question: You have previously installed the Google Cloud SDK on your work laptop and configured it. You now run the command gcloud compute instances create newvm but it does not prompt you to specify a compute/zone. Which of the following could explain this?

- [x] Your Google Cloud project includes default values for compute/region and compute/zone
  - _When you use the gcloud tool, you can omit setting the --region and --zone flags to use the default region and zone properties if they are set for your project. How a default region and zone affect your project._

#### Question: What is the easiest way to delete a project?

- [x] Run **gcloud projects delete oldprojid**
  - _You do not need to involve Support to delete a project; you just do that, yourself. Project budgets do not include any way to delete the project. If you rack up charges, you're liable for them even if you delete the project or it gets suspended._

#### Question: When should new projects be created?

- [x] Whenever the new project is needed
  - _Project creation does not involve any downtime. Google Support does not need to be involved in creating new projects. You can create a project and transfer ownership of it, if you need. Billing accounts can be linked and unlinked from projects and do not have to sync up with project lifetimes._

#### Question: You have just installed the Google Cloud SDK. Which of the following are the best way to initialize the command line tools?

- [x] gcloud init
- [x] Only one of the other options is required.
  - _It’s really quite straightforward to initialize gcloud: simply gcloud init and follow the prompts. And this also configures gsutil and bq._

#### Question: How many projects can you create?

- [x] As many as allowed by your quota
  - _You do have a quota for the total number of projects you can have at once._

#### Question: Which of the following are Google-recommended practices for creating new projects?

- [x] Create a project for each environment for your system--such as Dev, QA, and Prod.
- [x] Create separate projects for systems owned by different departments in your organization.
- [x] Use projects to limit blast radius.
  - _Creating new projects does not involve any downtime. Projects can be shared between all persons working with them; they do not have to be individual, and usually aren't. The system(s) in one project normally get deployed multiple times and serve many users. It's a good idea to use projects to separate different systems and environments from each other, partly for organization and partly to prevent them from interacting badly with each other._

#### Question: You already have a GCP project but want another one for a new developer who has started working for your company. How can you create a new project?

- [x] In the console, press on the current project name, then press on “Create New”.
  - _You can create new projects, up to your quota. Support does not create projects for you; that's something you do, yourself. “QUIK bindings” are just something made up._

#### Question:

- [x] 
  - 

#### Question:

- [x] 
  - 

#### Question:

- [x] 
  - 

#### Question:

- [x] 
  - 

## Planning and configuring a cloud solution

#### Question: You currently have 850TB of Closed-Circuit Television (CCTV) capture data and are adding new data at a rate of 80TB/month. The rate of data captured and needing to be stored is expected to grow to 200TB/month within one year because new locations are being added, each with 4-10 cameras. Archival data must be stored indefinitely, and as inexpensively as possible. The users of your system currently need to access 250TB of current-month footage and 100GB of archival footage, and access rates are expected to grow linearly with data volume. Which of the following storage options best suits this purpose?

- [x] Store new data as Regional and then use Lifecycle Management to transition it to Coldline after 30 days.
  - _Data cannot be transitioned from Multi-Regional to Regional through Lifecycle Management; that would change the location. The access rate for new data is 250/80--so quite high--but archival data access is very low (100/850000). Because of this, we need to start with Regional or Multi-Regional and should transition to Coldline to meet the “as inexpensively as possible” requirement._

#### Question: You currently have 850TB of Closed-Circuit Television (CCTV) capture data and are adding new data at a rate of 80TB/month. The rate of data captured and needing to be stored is expected to grow to 200TB/month within one year because new locations are being added, each with 4-10 cameras. Archival data must be stored indefinitely, and as inexpensively as possible. The users of your system currently need to access 60GB of current-month footage and 50GB of archival footage, and access rates are expected to grow linearly with data volume. Which of the following storage options best suits this purpose?

- [x] Immediately store all data as Coldline, because the access volume is low.
  - _Data cannot be transitioned from Multi-Regional to Regional through Lifecycle Management; that would change the location. The access rate for new data is 60/80000--so very low--and archival data access is even lower (50/850000). Because of this, the most cost-effective option is also the simplest one: just use Coldline for everything._


#### Question: You currently have 300TB of Closed-Circuit Television (CCTV) capture data and are adding new data at a rate of 80TB/month. The rate of data captured and needing to be stored is expected to grow to 200TB/month within one year because new locations are being added, each with 4-10 cameras. Archival data must be stored for six months, and as inexpensively as possible. The users of your system currently need to access 250TB of current-month footage and 150TB of archival footage, and access rates are expected to grow linearly with data volume. Which of the following storage options best suits this purpose?

- [x] Store new data as Multi-Regional and then use Lifecycle Management to transition it to Nearline after 30 days.
  - _Data cannot be transitioned from Multi-Regional to Regional through Lifecycle Management; that would change the location. The access rate for new data is 250/80--so quite high--but archival data access is lower--150/300. Because of this, we need to start with Regional or Multi-Regional (which are fairly close in price) and should transition to Nearline to meet the “as inexpensively as possible” requirement for archival data. And even though the option doesn’t list this, you would probably also want to set the Lifecycle Management to automatically delete the objects after their archival period expires._

#### Question: You need to visualize costs associated with a system you’ve been running on GCP. Which of the following is the best tool for this?

- [x] Data Studio
- [ ] GCP Pricing Calculator
- [ ] Cloud Billing API
- [ ] Cloud Pricing API
  - _The Billing API is about managing billing accounts, not about seeing or predicting costs. The Pricing API (actually, it’s the Catalog API) can give you information about what things would cost, but it would be a lot of work to turn that info into a system-level analysis. The pricing calculator is a critical tool to be familiar with, so make sure you study it before your exam, but it is not about historical costs. Data Studio is a great tool for visualizing historical costs._

#### Question: You need to estimate costs associated with a new system you plan to build on GCP. Which of the following is the best tool for this?

- [x] GCP Pricing Calculator
  - __

#### Question: You are planning to use BigQuery for a system you will manage. Which of the following statements best represents how you will use the pricing calculator?

- [x] You will separately estimate the data to be stored, streamed, and queried by your system and enter your estimated amounts into the GCP pricing calculator.
  - _There is not any such tool as the “BQ Data Analyzer” that does estimates and connects with the GCP Pricing Calculator. The GCP Pricing Calculator does not accept any sample data or queries; those need to be estimated separately. To estimate how much data a BQ Query will consider, use BQ’s “Dry Run” functionality._

#### Question: You need to process data streamed from Cloud Pub/Sub. Which of the following is a managed service that would handle this situation?

- [x] Cloud Dataflow
  - _Google does not have a service called “Cloud Storage Processing”. App Engine is not made to handle processing of this type. Cloud Dataproc is made for running Hadoop/Spark clusters but does not support streaming jobs. Cloud Dataflow is for newly-built processing that can take advantage of Apache Beam and supports both batch and streaming._

#### Question: You are planning a log analysis system to be deployed on GCP. Which of the following would be the best way to ingest the logs?

- [x] Google Cloud's operations suite (formerly Stackdriver)
  - _Google Cloud's operations suite provides integrated monitoring, logging, and trace managed services for applications and systems running on Google Cloud and other resources._

#### Question: You need to store some structured data and query and continually update it with SQL from your web app backend. The data volume and query load are reasonably consistent and you would like to reduce ongoing maintenance and management costs. Which option would best serve these requirements?

- [x] Cloud SQL
  - _Cloud Storage is for unstructured data and does not support SQL. BigQuery is made for mostly-static analytics situations--not continually updated data as indicated in the scenario--and a web app backend may need lower latency than BigQuery offers. Bigtable is made for low-latency analytics situations. Managing your own MySQL installation on GCE would be a lot more work than using Cloud SQL. Cloud SQL is a good fit for the described situation._

#### Question: The CTO aims to convert and migrate all of the legacy systems of the company to the usage of containers in GCP to take advantage of the benefits of container technology. Which of the following fits this use case well?

- [x] Kubernetes Engine
  - _For container requirements, the Kubernetes Engine (GKE) fits the use case very well._
  
#### Question: When comparing n1-standard-8, n1-highcpu-8, and n1-highmem-16, which of the following statements are true?

- [x] The n1-highmem-16 has twice as many CPUs as the n1-highcpu-8
- [x] The n1-highcpu-8 is the least expensive
  - _The number at the end of the machine type indicates how many CPUs it has, and the type tells you where in the range of allowable RAM that machine falls--from minimum (highcpu) to balanced (standard) to maximum (highmem). The cost of each machine type is determined by how much CPU and RAM it uses. Understanding that is enough to correctly answer this question._

#### Question: You are currently using an n1-highcpu-8 machine type and it is good but you would just like a bit more RAM. Which of the following is the most cost effective option to achieve this?

- [x] Switch to a custom machine type with 8 CPUs and more RAM
  - 

#### Question: You need to store thousands of 2TB objects for one month and it is very unlikely that you will need to retrieve any of them. Which of the following options would be the most cost-effective?

- [x] Nearline Cloud Storage bucket
  - _Bigtable is not made for storing large objects. Coldline’s minimum storage duration of 90 days makes it more expensive than Nearline. Multi-Regional and Regional are both more expensive than Nearline._

#### Question: A team has 3 running Cloud Functions with the same codebase for each of the 3 environments: development, staging, and production. The team does not want to hard code the secrets and variables inside the code to improve the reusability and portability of the codebase. How can the team accomplish this?

- [x] Environment Variables
  - _When using Cloud Functions, Environment Variables allow the user to provide key-pair values as configuration variables for the code when it is executed. The key to the question is that the team does not want to hard code the secrets and variables inside the code to improve the reusability and portability of the codebase. Only Environment Variables would meet those objectives._

#### Question: You currently have 850TB of Closed-Circuit Television (CCTV) capture data and are adding new data at a rate of 80TB/month. The rate of data captured and needing to be stored is expected to grow to 200TB/month within one year because new locations are being added, each with 4-10 cameras. Which of the following storage options best suits this purpose without encountering storage or throughput limits?

- [x] One Cloud Storage bucket for all objects
  - _This question might make you think you need to do some math to calculate rates and compare to limits, but you don’t. You don’t need to split your data up to avoid bucket-level limits. It is generally easiest (and best) to manage all your data in a single bucket and using things like folders for organizing them. In fact, if you separate data into many buckets, you are more likely to encounter limits around bucket creation and deletion._

#### Question: You need to store a large amount of unstructured data, including video, audio, image, and text files. The data volume is expected to double every 18 months and data access is sporadic and often clustered on a small portion of the overall data. You would like to reduce ongoing maintenance and management costs. Which option would best serve these requirements?

- [x] Cloud Storage
  - _Cloud Storage is perfect for unstructured data like this. BigQuery is made for analytics of structured data. Bigtable is made for low-latency analytics of non-relational data. Cloud SQL is not a good tool to store unstructured data like this and managing your own MySQL installation on GCE would be even worse._

#### Question: You need to host a legacy accounting process on SUSE Linux Enterprise Server 12 SP3. Which of the following is the best option for this?

- [x] GCE

#### Question: You need to store trillions of key/value data entries (2KB in size) for one month, and you will need to run analytical processing against all of them from hundreds of nodes. Which of the following options would be the most cost-effective?

- [x] Bigtable
  - _Bigtable is made for large analytical workloads. With Cloud Storage, you pay for read operations, so that can get quite expensive when it's not the right fit for the data and access patterns._

#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __

## Deploying and implementing a cloud solution

#### Question: Which of the following statements is true?

- [x] None of the other statements is true.
- [ ] Service Accounts should be used by GKE nodes and pods but not by GCE instances.
- [ ] You must specify a Service Account when creating an instance or none will be attached.
- [ ] Every instance must have a Service Account attached to it.
  - _If you don't do (or specify) anything, the default service account will be attached by default to each new GCE instance. However, you can stop that from happening by either deleting the default service account or opting out of attaching it when you are creating a new GCE instance._

#### Question: A team aims to create a storage bucket that stores files which are accessed once every 6 months. Which CLI command is used to perform this task?

- [x] gsutil mb -c coldline gs://
  - _Coldline is suitable for storage buckets accessed rarely. To create a bucket the gsutil mb command is used._

#### Question: A Java program running on a GCE instance needs access to the Cloud Tasks API. Which of the following is NOT something Google would recommend for this configuration?

- [x] The program should pass “Metadata-Flavor: Google” to the SDK
- [ ] The GCE instance should be using a service account
- [ ] The service account should have access to the Cloud Tasks API
- [ ] The access scopes should include access to the Cloud Tasks API
- [ ] The program should use the Google SDK
  - _Java programs can use the SDK to access GCP services, and the SDK will take care of the details of retrieving the access token from the metadata service and communicating with the service. As such, your program does not need to concern itself with the “Metadata-Flavor: Google” header; the SDK will handle that._

#### Question: You are monitoring a GKE cluster and see that a pod is being terminated. What will happen?

- [x] The memory used by the containers will be freed.
  - _There are such things as deployments and StatefulSets, but they don’t have domains or ports, respectively. GKE doesn’t have such a thing as a PersistentSet, but it does have DaemonSets._

#### Question: You want to create a new regional bucket in Iowa. How could you go about doing this?

- [x] Begin creating the bucket, set the bucket name, set the Location type to Region, and select the us-central1(Iowa) Location, and choose CREATE.
  - _The steps to create a bucket in Iowa would be: Begin creating the bucket, set the bucket name, set the Location type to Region, and select the us-central1(Iowa) Location, and choose CREATE._

#### Question: You are thinking through all the things that happen when a Compute Engine instance starts up with a startup script that installs the Stackdriver agent and runs gsutil to retrieve a large amount of data from Cloud Storage. Of the following steps, which is the first one to happen?

- [x] The metadata service returns information about this instance to the first requestor

#### Question: You are thinking through all the things that happen when a Compute Engine instance starts up with a startup script that installs the Stackdriver agent and runs gsutil to retrieve a large amount of data from Cloud Storage. Of the following steps, which is the last one to happen?

- [x] Data retrieval from GCS completes
  - _Immediately when the VM is powered on, resources are allocated and acquired, the OS starts booting up, and the instance is considered to be Running. That's when gcloud completes, if it was run without --async. Then the metadata service will provide the startup script to the OS boot process. The gsutil command will also need to get metadata--like the service account token--but since it is synchronous by default and will take some time to transfer the volume of data to the instance, the Stackdriver agent should have a chance to push logs and show the startup script progress. When the transfer is done, the startup script will complete and more logs will eventually be pushed to Stackdriver Logging._

#### Question: You need to very quickly set up Nginx Plus on GCP. Which of the following is the fastest option to get up and running?

- [x] GCP Marketplace
  - _Nginx cannot run on Cloud Functions, nor on App Engine Standard. Setting it up on Kubernetes Engine would take rather more time/effort than using the marketplace. The GCP Marketplace is a quick way to deploy all sorts of different systems, including Nginx Plus._

#### Question: Which of the following command line options can be used to create a bucket in Cloud Storage?

- [x] gsutil
  - __

#### Question: You need to very quickly set up Wordpress on GCP. Which of the following are the fastest options to get up and running?

- [x] GCP Marketplace
- [x] Cloud Launcher
  - _There is no such GCP service as “Cloud Press”. Wordpress is not designed to run on Google Cloud Functions. The Cloud Launcher was renamed to be the GCP Marketplace--so these refer to the same thing--and this is a quick way to deploy all sorts of different things in GCP. _

#### Question: What will happen if a running GKE node encounters a fatal error?

- [x] GKE will automatically restart that node on an available GCE host.
  -  _Nodes are GCE instances managed by the GKE system. If one of the nodes dies, GKE will bring another node up to replace it and will ensure that any affected pods are restarted._

#### Question: What will happen if a running GKE pod encounters a fatal error?

- [x] If it is a part of a deployment, GKE will automatically restart that pod on an available node.
  - _GKE tries to ensure that the number of pods you’ve specified in your deployment are always running, so it will restart one if it fails. All the other options are using terms in ways that don’t make sense (such as “an available deployment”). From the documentation: Pods do not 'heal' or repair themselves. For example, if a Pod is scheduled on a node which later fails, the Pod is deleted. Similarly, if a Pod is evicted from a node for any reason, the Pod does not replace itself._

#### Question: You are planning to run a single-node database on GKE. Which of the following things do you need to consider?

- [x] You should use PersistentVolume and PersistentVolumeClaim objects
  - _Databases are all about preserving information--about keeping and not losing data--so we need to make sure that GKE knows that we care about the data we store and need to keep it around. To do this, we need Persistent Volumes and Persistent Volume Claims. GKE does not replicate disks across pods; it ensures that the data for a pod persists and is still available to it when it recovers from a failure. _

#### Question: You need to set up Lifecycle Management on a new Cloud Storage bucket. Which of the following options should you consider?

- [x] Identify an existing bucket with the configuration you want, download that bucket’s configuration JSON using the JSON API, apply the configuration file for the new bucket via gsutil.
  - _There are some details here that you just need to remember: 1) The GCS console does not deal with Lifecycle configuration files, 2) gsutil deals with JSON files, and 3) the JSON and XML APIs each deal with JSON and XML, respectively. _

#### Question: You run the command kubectl deploy-pod mypodname in Cloud Shell. What should you expect to see?

- [x] An “unknown command” error
  - _This is not a valid command and kubectl will complain that it is unknown. [Cheat Sheet for kubectl](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) [Viewing Pods and Nodes in Kubernetes](https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/)_

#### Question: You are planning to run a multi-node database on GKE. Which of the following things do you need to consider?

- [x] You should use a StatefulSet object
  - _There is no such thing as a PodReplicationState object, in Kubernetes. Data will be persisted in Persistent Volumes even if all DB pods have failed or been shut down. Kubernetes StatefulSet objects exist to manage applications that do want to preserve state--unlike the normal applications that should be stateless. Deploying a Stateful Application on GKE Why StatefulSets and not just persistent volumes?_

#### Question:

- [x] 
  - __


## Ensuring successful operation of a cloud solution

#### Question: After an initial audit of the resources of an existing Kubernetes cluster, the DevOps team of a company has noticed that pods for workloads running a staging environment are still running after an initial deletion of all pods. The DevOps team has performed the pod deletion operation but new pods get created to replace the deleted pods. How can the team remove these pods permanently?

- [x] Delete the ReplicaSet
  - _The ReplicaSet automatically creates the pods to maintain the desired state (e.g. number of pods/replicas). If the ReplicaSet is not deleted and only the pods are deleted directly, the number of pods will continue to meet the desired state. All other options will not solve this requirement. _

#### Question: You are designing the logging structure for a non-containerized Java application that will run on GCE. Which of the following options is recommended and will use the least number of steps to enable your developers to later access and search logs?

- [x] Have the developers write log lines to a file named application.log, install the Stackdriver agent on the VMs, configure the Stackdriver agent to monitor and push application.log
  - _The App Engine SDKs only work for apps running on App Engine. Stackdriver does not automatically send files named stackdriver.log . Stackdriver is not installed by default on GCE. Logging to stdout and stderr on GCE is not the recommended way to get logs to Stackdriver; configuring a custom log file location is._

#### Question: You are designing the logging structure for a containerized Java application that will run on GAE Flex. Which of the following options is recommended and will use the least number of steps to enable your developers to later access and search logs?

- [x] Have the developers write log lines to stdout and stderr
  - _In App Engine Flex the connection to Stackdriver (i.e. agent installation and configuration) is handled automatically for you. In GAE Flex, you could write logs using the App Engine SDK--and that would work--but it’s best practice for containers to log to stdout and stderr, instead: “Containers offer an easy and standardized way to handle logs because you can write them to stdout and stderr. Docker captures these log lines and allows you to access them by using the docker logs command. As an application developer, you don't need to implement advanced logging mechanisms. Use the native logging mechanisms instead.” _

#### Question: Your team is running a Kubernetes cluster in GCP. One of the engineers has created a service that acts as a load balancer to several pods. Unfortunately, the setup does not work and the load balancer does not seem to detect the target pods. The engineer was instructed to list down the labels of the pods running in the cluster to troubleshoot this issue. How can the engineer accomplish this?

- [x] kubectl get pods --show-labels

#### Question: A medium-sized company has been running multiple pods in multiple namespaces in GCP. A junior service reliability engineer has used the command to list all pods but some of the running pods from other namespaces do not show up in the results. How can the junior engineer list down the pods from other namespaces as well?

- [x] kubectl get pods --all-namespaces

#### Question: A new hire from the engineering team was given a task of debugging the contents of a Kubernetes secret as a YAML file. How can the new hire accomplish this?

- [x] kubectl get secret -o yaml

#### Question: An associate engineer needs to scale a Replica Set named 'target-replicaset' to 5. Which command will allow the associate engineer to accomplish this task?

- [x] kubectl scale --replicas=5 rs/target-replicaset
  - _The kubectl scale command is used to scale the replicaset from the command line._

#### Question: A team is planning to analyze the network logs of an application that has been running for a couple of weeks. Which of the following enables the team to perform this analysis?

- [x] Flow Logs
  - _The flow logs contain the network logs of the network environment which can be used for analysis_

#### Question: A CloudSQL database is experiencing more read transactions recently due to the increasing need for admin reports by a system. Which of the following can be used to reduce the load issues experienced by the system?

- [x] Read Replicas

#### Question: You have a StatefulSet and a DaemonSet deployed in your GKE cluster which currently has seven nodes. What will happen if you scale the cluster down to six nodes?

- [x] The number of pods for the DaemonSet will shrink.
  - _A DaemonSet runs one pod per GKE node._

#### Question: You have a GKE cluster that currently has six nodes but will soon run out of capacity. What should you do?

- [x] In the GKE console, edit the cluster and specify the new desired size.
  - _Clusters are editable, not immutable, and should not be recreated because of changes in demand. Cluster autoscaling is an optional setting. You do not manage nodes via GCE, directly--you always manage them through GKE, even though you can see them via GCE._

#### Question: A team is running multiple production workloads in GCP. Due to the number of issues experienced by the team for the past 3 weeks, the Operations Head has asked the SRE team to send all stack traces and error crashes to a centralized service to help manage these issues. How can the team accomplish this?

- [x] Stackdriver Error Reporting
  - _When dealing with stack traces, Stackdriver Error Reporting is the option to choose._

#### Question: An associate engineer was instructed to change an empty Cloud Storage bucket from one region to another. How can the associate engineer accomplish this?

- [x] Delete the original bucket. Create a new bucket in the target region.
  - _A new bucket must be created as the region can not be modified after a bucket is created._

#### Question: You run the command kubectl describe pods mypodname in Cloud Shell. What should you expect to see?

- [x] Information about the named pod
  - _This is a valid command and Cloud Shell will automatically configure kubectl with the required authentication information to allow you to interact with the GKE cluster through it._

#### Question: A service reliability engineer has been instructed to generate a Kubernetes secret for a staging Kubernetes cluster. The engineer was given a .env.staging file that contains key-value pairs inside a file which is loaded by the application. How can the service reliability engineer accomplish this?

- [x] kubectl create secret generic --from-file=.env.staging
  - _One of the options to generate a secret from a file is with the use of the --from-file flag. All other options will not solve this requirement._

#### Question: An engineer needs to present a PoC (Proof of Concept) work to the team's Deployment Head that demonstrates the capabilities of Kubernetes in GCP. The engineer plans to create new resources from a file accessible in a URL such as Github. How can the engineer accomplish this?

- [x] kubectl apply -f
  - _The YAML config can be used directly from a URL and the same kubectl apply -f command is used with the URL as the parameter._

#### Question: A Kubernetes cluster is running a pod named 'target-pod' that has been running for at least 2 days. The team has realized that the try-catch block in the backend API is simply printing out and logging the errors in the API's container which is causing data integrity issues for the application. The lead engineer needs shell access to the container to check the printed errors. Which command will give the lead engineer access to the container?

- [x] kubectl exec -it target-pod -- /bin/bash
  - _To get ssh access to the pod, the kubectl exec -it command is used. All other options are not possible. All other options will not solve this requirement. _

#### Question: You need to view both request and application logs for your Python-based App Engine app. Which of the following options would be best?

- [x] Use the built-in support to get both request and app logs to Stackdriver.
  - _Google App Engine natively connects to Stackdriver and sends both request logs and any application logs you give it (via the GAE SDK). _

#### Question: A Kubernetes cluster with 4 nodes is running production workloads for a couple of months. The team managing the cluster was instructed to install a monitoring agent on all nodes of the cluster. Which Kubernetes API resource can be used to accomplish this task?

- [x] DaemonSet
  - _DaemonSet is used to ensure that a specific process is running on all nodes. All other options will not solve this requirement. Kubernetes: DaemonSet_

#### Question: You have a GKE cluster that has fluctuating load over the course of each day and you would like to reduce costs. What should you do?

- [x] In the GKE console, edit the cluster and enable cluster autoscaling.
  - _Clusters are editable, not immutable, and should not be recreated because of changes in demand. You cannot manage GKE nodes with your own instance groups--and you can’t migrate nodes into a managed instance group, anyway. You cannot enable cluster autoscaling with the resize command, but you can turn that option on in the console or using the command gcloud container clusters update CLUSTER_NAME --enable-autoscaling_

#### Question:

- [x] 
  - __

## Configuring access and security

#### Question: Which of the following roles has the highest level of access?

- [x] Project Owner
  - _There are no such roles as Organization Superuser, Organization Auditor, nor Controller. The Project Owner has all of the capabilities of the other two (Project Editor and Compute Administrator), and more. (There is, however, a “Super Admin” role for an organization that can control everything.)_

#### Question: You are working together with a contractor from the Acme company and you need to allow App Engine running in one of Acme’s GCP projects to write to a Cloud Pub/Sub topic you own. Which of the following pieces of information are enough to let you enable that access?

- [x] The email address of the Acme project service account
- [x] The Acme GCP project’s project ID
  - _You need to grant access to the service account being used by Acme’s App Engine app, not the contractor, so you don’t care about the contractor’s email address. If you are given the service account email address, you’re done; that’s enough. If you need to use the pattern to construct the email address, you’ll need to know the Project ID (not its number, unlike for GCE!) to construct the email address used by the default App Engine service account: _

#### Question: How should you enable a GCE instance to read files from a bucket in the same project?

- [x] Only one of the other options is correct
- [x] Do not change the default service account setup and attachment
- [ ] Log onto the instance and run gcloud services enable storage.googleapis.com
- [ ] Grant bucket read access to the default compute service account
- [ ] Log into Cloud Shell and run gcloud services enable storage.googleapis.com
- [ ] When launching the instance, remove the default service account so it falls back to project-level access
  - _By default, both the default service account and the default scopes can read from GCS buckets in the same project, so you should just leave those alone and it will work._

#### Question: Which IAM permission allows a user to modify the Cloud Storage ACLs?

- [x] storage.objects.setIamPolicy
  - __

#### Question: You navigate to the Activity Log for a project containing a GKE cluster you created. If you select VM Instance for the filter option, which would be an example of output you should see?

- [x] 843749848358@cloudservices.gserviceaccount.com created gk3-autopilot-cluster-1-default-pool-569d40f6-dw8l
  - _Log lines for GKE node creation will show up in the activity log. The Google-managed API Service Agent account creates such entries, not the user’s account or the GCE service account._

#### Question: You need to list objects in a newly-created GCS bucket. Which of the following would allow you to do this?

- [x] roles/storage.legacyBucketReader
- [x] roles/owner

#### Question: You are designing the object security structure for sensitive customer information. Which of the following should you be sure to include in your planning?

- [x] Assign only limited access, to achieve least privilege

#### Question: You have a GCE instance using the default service account and access scopes allowing full access to storage, compute, and billing. What will happen if an attacker compromises this instance and runs their own program on it?

- [x] None of the other options is correct. 
  - _Requiring the “Metadata-Flavor: Google” header protects against a different type of attack than the one described in this question, so it will not help in this case. The access token will be available to the attacker’s program and it will work the same way from outside of GCP as it does from within it, regardless of the MAC address. In particular, the token will only allow the attacker (as any user) to perform whatever is allowed by both the service account and the access scopes. Since both the service account and the access scopes are missing some capabilities from the other, the actual access possible by using the token will be less than either of them, independently. _

#### Question: You are designing the object security structure for sensitive customer information. Which of the following should you be sure to include in your planning?

- [x] Do not grant any bucket-level permissions, so that new objects are secure by default.
  - _Separation of duties is not about who can read and who can write data. Security should be simple, yes, but it needs to actually be secure, first. You should generally not design your system to need so many buckets, and you can properly secure the data with object-level ACLs. It can be a good strategy to not allow any bucket-level access and force access to be granted explicitly at the object level. _

#### Question: You are planning out your usage of GCP. Which of the following things do you need to consider about Service Accounts?

- [x] The default service account is restricted in what it can do by the default access scopes.
  - _The scopes that restrict what can be done through a service account are somewhat limited, by default._

#### Question: Can you generate access keys for service accounts?

- [x] Yes. You may generate a small number of keys per service account to facilitate key rotation.
  - _It is best when you let Google manage all service account keys, but it is possible to generate some so you can use them outside of the situations that GCP handles--such as from AWS or your local machine. You don’t need to remember how many keys you can generate (10), only that the reason you can create more than one is so that you can put a new one in place before disabling an old one (i.e. key rotation)._

#### Question: You are planning out your organization’s usage of GCP. Which of the following is a Google-recommended practice?

- [x] None of the other options is correct.
- [ ] GCS ACLs should always be set by a Service Account.
- [ ] GCS ACLs should always be set to a Service Account.
- [ ] Auditor access should be granted through a Service Account.
- [ ] The project owner should generally be a Service Account.
  - _Service accounts are meant to be used by programs and they are one--but not the only!--way to manage access to resources._

#### Question: You need to determine who just started a particular GCE instance that does not meet your organization’s resource labelling policies. How can you determine who to follow up with, in the least number of steps?

- [x] From the notifications menu, navigate to the Activity Log. Look for the log line, “Create VM”.
  - __

#### Question: You go to the Activity Log to look at the “Create VM” event for a GCE instance you just created. You set the Resource Type to “GCE VM Instance”. Which of the following will display the “Create VM” event you wish to see?

- [x] Set the “Activity Types” dropdown to “Configuration”
  - _You must become very familiar with the Activity Log. In this case, “Create VM” is considered to be a “Configuration” activity._

#### Question: A team needs to be given granular access to a GCP service because of the need to protect very sensitive data in the account. The team is also avoiding the usage of custom roles and prefers GCP managed roles for this account. Which IAM role would fit this use case?

- [x] Predefined
  - _For requirements that involve GCP managed roles while avoiding the usage of custom roles, the Predefined roles would fit the use case._

#### Question: A co-worker tried to access the myfile file that you have stored in the mybucket GCS bucket, but they were denied access? Which of the following represents the best way to allow them to view it?

- [x] In Cloud Shell, type gsutil acl ch -u coworker@email.domain:r gs://mybucket/myfile
  - _There is no “Add Exception” button on the Activity screen. Neither will gcloud storage allow-access work. You could add the co-worker as a project editor, but that is way more privilege than they need to view one file._
