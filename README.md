# terraform-aws-infra-model

---

## Features

*   **Simple S3 Bucket Provisioning:** Creates a single `aws_s3_bucket` resource.
*   **Tagging Support:** Allows for easy application of resource tags for cost allocation and organization.
*   **Makefile Automation:** Provides targets for `init`, `plan`, `apply`, and `destroy` for both `dev` and `prod` environments.

## Usage

The module can be included in your Terraform configuration as follows:

```terraform
module "my_s3_bucket" {
  source = "github.com/kelasih/terraform-aws-infra-model//infra/terraform/modules/aws/s3"

  bucket_name = "my-unique-bucket-name-12345"
  tags = {
    Environment = "Production"
    Project     = "InfraModel"
  }
}

output "bucket_name" {
  value = module.my_s3_bucket.bucket_name
}
```

## Requirements

The following tools are required to use the automation provided in this repository:

| Name | Version | Notes |
| :--- | :--- | :--- |
| **Terraform** | `~> 1.0` | Used for infrastructure provisioning. |
| **AWS CLI** | `~> 2.0` | Required for AWS authentication and configuration. |
| **make** | Any | Used to execute the automation targets defined in the `Makefile`. |

## Automation with Makefile

The repository includes a comprehensive `Makefile` in the `infra/` directory to simplify common operations across different environments (`dev` and `prod`).

### Common Targets

Targets are prefixed with the environment name (e.g., `dev-init`, `prod-plan`).

| Target | Description | Command |
| :--- | :--- | :--- |
| `dev-init` | Initializes the Terraform working directory for the `dev` environment. | `tf,dev,init` |
| `dev-plan` | Generates and shows an execution plan for the `dev` environment. | `tf,dev,plan` |
| `dev-apply` | Applies the changes required to reach the desired state for `dev`. | `tf,dev,apply` |
| `dev-destroy` | Destroys the infrastructure managed by the `dev` environment. | `tf,dev,destroy` |
| `prod-init` | Initializes the Terraform working directory for the `prod` environment. | `tf,prod,init` |
| `prod-plan` | Generates and shows an execution plan for the `prod` environment. | `tf,prod,plan` |
| `prod-apply` | Applies the changes required to reach the desired state for `prod`. | `tf,prod,apply` |
| `prod-destroy` | Destroys the infrastructure managed by the `prod` environment. | `tf,prod,destroy` |

## License

This project is licensed under the **Apache-2.0 License**. See the [LICENSE](LICENSE) file for details.
