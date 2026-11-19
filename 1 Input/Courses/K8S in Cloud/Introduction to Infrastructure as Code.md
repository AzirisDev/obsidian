	Lets first set a budget in subscription in Azure

It is better set a budget with alert on 50% and 75% spend of the actual budget, so that we can track our spendings.

#### What is IaC?
`IaC` means describing infrastructure via code declaratively pointing to the desired state. We get version control, history of changes, drift detection, disaster recovery.

#### What type of tools do we have for IaC?
1) **Terraform** is industry standard. You write HCL, a purpose-built declarative language. Its strengths are:
- **Cloud agnostic.**
- **Huge ecosystem of providers.** One `terraform apply` can create a cloud database _and_ the monitoring alert for it.
The **state file** is its defining trait and its main operational burden. Terraform records what it manages in `terraform.tfstate`. In a team you must store that file remotely (an S3 bucket, Azure Storage, Terraform Cloud) with locking. Otherwise two people applying at once can corrupt it. The file can also contain secrets, so it needs protecting.

2) **Bicep (Microsoft, Azure only)** is a cleaner language that compiles down to ARM templates, Azure’s native JSON format. Its advantages are:
- **Always compatible / latest API.** A new Azure feature is usable in Bicep on day one. Terraform’s azurerm provider sometimes lags
- **No state file.** Azure Resource Manager itself is the source of truth, so there is nothing to store or lock.
- **Easier to learn**

3) **Pulumi** is IaC in real programming languages: TypeScript, Python, Go, C#, Java. Instead of HCL you get loops, functions, classes, unit tests, IDE autocomplete and package managers. It’s multi-cloud like Terraform.

4) **Crossplane (CNCF)** is a different model entirely. It extends **Kubernetes** so that cloud resources become Kubernetes objects. You `kubectl apply` a YAML manifest describing an RDS database, and Crossplane’s controllers create it in AWS. They then **continuously reconcile** it: if someone changes it by hand, Crossplane puts it back. There’s no state file, because the Kubernetes API (etcd) holds the desired state. It fits naturally with GitOps tools like Flux and Argo CD, since they’re already syncing YAML into a cluster. The cost is that you need a running Kubernetes cluster to manage your infrastructure, which is a chicken-and-egg problem for the cluster itself.

5) **AWS CloudFormation** is AWS’s native equivalent of Bicep/ARM. You write YAML or JSON templates and deploy them as **stacks**. Like Bicep, there’s no state file to manage, since AWS tracks the stack. It also does automatic rollback on failure and has deep integration with AWS services.

#### [[Setup Terraform]]

Links:

202611181419

