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

## Planning and configuring a cloud solution

#### Question: You currently have 850TB of Closed-Circuit Television (CCTV) capture data and are adding new data at a rate of 80TB/month. The rate of data captured and needing to be stored is expected to grow to 200TB/month within one year because new locations are being added, each with 4-10 cameras. Archival data must be stored indefinitely, and as inexpensively as possible. The users of your system currently need to access 250TB of current-month footage and 100GB of archival footage, and access rates are expected to grow linearly with data volume. Which of the following storage options best suits this purpose?

- [x] Store new data as Regional and then use Lifecycle Management to transition it to Coldline after 30 days.
  - _Data cannot be transitioned from Multi-Regional to Regional through Lifecycle Management; that would change the location. The access rate for new data is 250/80--so quite high--but archival data access is very low (100/850000). Because of this, we need to start with Regional or Multi-Regional and should transition to Coldline to meet the “as inexpensively as possible” requirement._

#### Question: You currently have 850TB of Closed-Circuit Television (CCTV) capture data and are adding new data at a rate of 80TB/month. The rate of data captured and needing to be stored is expected to grow to 200TB/month within one year because new locations are being added, each with 4-10 cameras. Archival data must be stored indefinitely, and as inexpensively as possible. The users of your system currently need to access 60GB of current-month footage and 50GB of archival footage, and access rates are expected to grow linearly with data volume. Which of the following storage options best suits this purpose?

- [x] Immediately store all data as Coldline, because the access volume is low.
  - _Data cannot be transitioned from Multi-Regional to Regional through Lifecycle Management; that would change the location. The access rate for new data is 60/80000--so very low--and archival data access is even lower (50/850000). Because of this, the most cost-effective option is also the simplest one: just use Coldline for everything._

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

## Deploying and implementing a cloud solution

#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
#### Question: 

- [x] 
  - __

#### Question: 

- [x] 
  - __
