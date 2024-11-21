# This is list of lesson learnt from creating streaming project in AWS with cdk and github action

## Insight
- 21/11/2024
    - how do i connect the dot for aws infra?
        - i.e. what resource is under certain VPC and how do connection setting there?

- 20/11/2024
    - sharing by Arockia
    - to remove cdk bootstrap from main flowchart as industry assumed it is basic mandatory setup and not part of design
    - industry practice is 
        - to create multiple projects. E.g.
            - project1: only for bootstrap
            - project2 and so forth: expand create resource independently
            - each project (2 and so on) communicate resource and creds using `SSM parameter` or `secrets manager`
        - use different aws account for different environment
        - in github workflow yml:
            - every env can be define in orderly manner (after dev success, continue step on test and so forth)
            - or some might deploy dev and then work on other env (no direct dependency)
        - each resource should have own s3 bucket to store audit log or use cloudwatch
            - enable resource property/method (i.e. S3 -> `serveraccesslog`)
            - create bucket and point method to that bucket
        - each resource/role must have tag
        - create authorization
            - lambda authrization before api gateway where only hardcoded key / custom method can access else invoke error message

- 19/11/2024
    - there are two method to create usable resource:
        - use function
        - use construct
    - by default, cdk create:
        - predefined role to handle CLoudFormation stack
        - s3 bucket to store config and metadata of project

- 18/11/2024
    - I accidental delete predefined role in IAM GUI
        - rerun bootstrap solve the issue as it recreated preconfigured setting
        - impact of delete predefined role is I cannot delete CloudFormation stack

    - Beware of what method use (https or rest api) in API Gateway:
        - different method will have different variables format in event (for lambda handler(event,context))
        - i.e. restApi use httpMethod but https use http-method

- 14/11/2024