# AWS Organizations Configuration Module
This module aids in configuration and management of the AWS Organizations Service and sub-entities such as "Accounts" and "Organizational Units."

Please note that there are special consideration / manual steps that may be required in certain scenarios such as enabling / disabling features on pre-existing organizations. See [provider documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/organizations_organization) or [AWS Organizations User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) for more details.

## Getting Started
TODO - basic instructions / prerequisites
* AWS Account in which Organization is to be created/configured

## Contributing

## Module List / Documentation
TODO - https://github.com/terraform-docs/terraform-docs

* AWS Email Processor
  * lambda / SES configuration for ingest/management of AWS Account Email(s)
  * rules-based routing - "is this a billing email? security? PSE?" - possibly allow for lookup of resource tags of any mentioned resources & include as "TO"

* AWS Tag Policy
  * Sets up common structures for enforcement of tag policy
  * Allows for dynamic calculation / updating of valid tag values (some kind of lambda + key/value list; key/value list to be updated externally; probably requires authz concept at least at a row level in DB / prefix level - but how would this be different than just updating the policy directly?)

* AWS Service Control Policy
  * Helps with common structures / approaches to SCP
  * Define / enforce Tag Requirement(s)

* AWS Organizational Unit
  * TBD

* AWS Account - (TODO: Determine what should be encapsulated into the "module" and what should be feature-flagged / extracted)
  * Inputs:
    * emails - root, alternate contact(s)
    * name
    * tag(s)
    * OU
    * Billing Limit
  * Resources Created:
    * IAM Permission Boundary blocking access to protected resource(s)
    * IAM Role / Policy for delegated owner access
    * CloudTrail + S3 Target Bucket
    * Billing Limits / Alerts
    * Automated Resource TTL / Cleanup
    * Config Rule(s)
