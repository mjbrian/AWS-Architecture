# Core Services

## TOC

1. [Schema](#Schema)
1. [Authentication](#Authentication)
1. [Request](#Request)
1. [Authorization](#Authorization)
1. [Best Practices](#Best-Practices)
1. [User Auditing](#User-Auditing)
1. [Configuring Alarms and Notifications](#Alarms-Notifications)

## Schema

`Principal` (App || User) => `Authentication` => `Request` => `Authorization`

## Authentication

`Authentication` => `UserName & Password` || `Programmatic Keys`
`Authentication` => `Request`

## Request

A `Request` consists of:

- Action(s)
- Resource(s)

## Authorization

Access Policy

## Best practices

- sign-up for an acct
- create alt account for users (skipped due to already complete)
- create a group `MBSuperUsers`
  - assign `AdministratorAccess` policy
  - end result:

    ```json
    {
        "Version": "2020-1-1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": "*",
                "Resource": "*"
            }
        ]
    }
    ```

- create a user for myself
  - add user to the group we created
- [enable MFA](https://aws.amazon.com/iam/features/mfa/)
  - `IAM Console` => `Security Status` => `Manage MFA` => Follow the MFA Wizard
  ![AWS Diagram](/images/iam-mfa.png)
- Set Password Policy
  - `IAM Console` => `Account Settings` => Enable:
    - `Minimum Password Length`
    - `Require at least one uppercase letter`
- All Best practices should be satisfied
![Best Practices](/images/iam-best-practices.png)

## User Auditing

Cloud Trail is an event viewer & auditing tool for AWS.

## Alarms Notifications

AWS Services > Management Tools > `CloudWatch`

### Enable billing alerts

Prerequisite: `Receive Billing Alerts` must be enabled in the `Account Billing Console`.
