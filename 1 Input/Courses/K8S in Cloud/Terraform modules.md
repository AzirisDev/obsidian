A **Terraform module** is a reusable, self-contained package of Terraform configuration: a folder of `.tf` files that groups related resources so you can call them as one unit, like a function in programming.

Without modules you end up copy-pasting the same 50 lines for every VPC, cluster, or bucket. With a module you write that logic once, expose a few inputs, and reuse it across environments (dev, staging, prod) or projects. This keeps code consistent, cuts duplication, and lets teams share standard building blocks.

**Anatomy of a module**
A typical module folder looks like this:

```
modules/s3-bucket/
├── main.tf        # resources
├── variables.tf   # inputs (like function parameters)
├── outputs.tf     # values returned to the caller
└── versions.tf    # provider/version constraints
```

```hcl
# modules/s3-bucket/variables.tf
variable "name" { type = string }
variable "versioning" {
  type    = bool
  default = true
}

# modules/s3-bucket/main.tf
resource "aws_s3_bucket" "this" {
  bucket = var.name
}

resource "aws_s3_bucket_versioning" "this" {
  bucket = aws_s3_bucket.this.id
  versioning_configuration {
    status = var.versioning ? "Enabled" : "Suspended"
  }
}

# modules/s3-bucket/outputs.tf
output "arn" { value = aws_s3_bucket.this.arn }
```

**Calling it from the root module**

```hcl
module "logs_bucket" {
  source     = "./modules/s3-bucket"
  name       = "my-app-logs"
  versioning = false
}

# use its output elsewhere
output "logs_arn" {
  value = module.logs_bucket.arn
}
```

After adding or changing a module source, run `terraform init` so Terraform downloads or links it.

Check this link for Terraform modules: https://github.com/AzirisDev/mercury-workflows/tree/main/phase-2-modules

Links:

202611191849

