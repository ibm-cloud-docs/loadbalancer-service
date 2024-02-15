---

copyright:
  years: 2021
lastupdated: "2021-05-19"

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Setting up Terraform for IBM Cloud Load Balancer
{: #terraform-setup}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent provisioning of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multitier cloud environments following Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API and SDKs, you can automate the provisioning, update, and deletion of your load balancer instances by using HashiCorp Configuration Language (HCL).
{: shortdesc}

Looking for a managed Terraform on {{site.data.keyword.cloud}} solution? Try out [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started). With {{site.data.keyword.bpshort}}, you can use the Terraform scripting language that you are familiar with, but you don't must worry about setting up and maintaining the Terraform command line and the {{site.data.keyword.cloud}} Provider plug-in. {{site.data.keyword.bpshort}} also provides pre-defined Terraform templates that you can easily install from the {{site.data.keyword.cloud}} catalog.
{: tip}

## Installing Terraform and configuring resources for IBM Cloud Load Balancer
{: #install-terraform}

1. Follow the [Terraform on {{site.data.keyword.cloud}} getting started tutorial](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started) to install the Terraform CLI and configure the {{site.data.keyword.cloud}} Provider plug-in for Terraform. The plug-in abstracts the {{site.data.keyword.cloud}} APIs that are used to provision, update, or delete IBM Cloud Load Balancer service instances and resources.
2. Create a Terraform configuration file that is named `main.tf`. In this file, you add the configuration to create a load balancer and to assign a user an access policy in Identity and Access Management (IAM) for that instance by using HashiCorp Configuration Language (HCL). For more information, see the [Terraform documentation](https://developer.hashicorp.com/terraform/language){: external}.

   The load balancer instance in the following example is named `test_lb_local_service` and is enabled on port `80`. The ID of the local load balancer service group is `ibm_lb_service_group.test_service_group.service_group_id` and the weight for the load balancer service group is `1`. 
   
   For more information, see the [ibm_lb_service](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/lb_service){: external} usage example.
   {: note}

   ```sh
   resource "ibm_lb_service" "test_lb_local_service" {
    port = 80
    enabled = true
    service_group_id = ibm_lb_service_group.test_service_group.service_group_id
    weight = 1
    health_check_type = "DNS"
    ip_address_id = ibm_compute_vm_instance.test_server.ip_address_id
    }
   ```
   {: codeblock}

3. Initialize the Terraform CLI.

   ```sh
   terraform init
   ```
   {: codeblock}

4. Create a Terraform execution plan. The Terraform execution plan summarizes all the actions that need to be run to create the load balancer in your account.

   ```sh
   terraform plan
   ```
   {: codeblock}

5. Create the load balancer instance and IAM access policy in {{site.data.keyword.cloud_notm}}.

   ```sh
   terraform apply
   ```
   {: codeblock}

6. From the [{{site.data.keyword.cloud_notm}} resource list](/resources){: external}, select the load balancer instance that you created and note the instance ID.
