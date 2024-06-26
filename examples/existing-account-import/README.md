# Existing account example

If an AWS account has been imported, the `iam_user_access_to_billing` setting must be set to "NULL" (`string`)
This is because it can only be set during account creation

## Importing an account

```
terraform import 'module.aws_organizations_and_sso.aws_organizations_account.account["my-account-name"]' 0123456789112
```

```
module "aws_organizations_and_sso" {
  source  = "chris-qa-org/organzation-and-sso/aws"
  version = "1.1.3"

  organization_config = {
    units = {
      "my-org-unit" = {
        accounts = {
          "my-account-name" = {
            email                      = "me@example.com"
            iam_user_access_to_billing = "NULL"
          }
        }
      }
    },
    feature_set          = "ALL",
    enabled_policy_types = []
  }
}
```
