# Record of project structure change over time

## 20/11/2024
- Arockia advised to change folder structure:
    - every resoruce to deploy need to be under lib including:
        - custom constructor, policies, client and data 

```
cdk-github-action
├── .github/
│   └── workflows/
│       └── deploy.yml
├── bin/
│   └── cdk-github-action.ts
├── client/
│   └── test-api-gateway.py
├── data/
│   └── TestSample.csv
├── lambda/
│   ├── api_gateway_to_kinesis.py
│   └── kinesis_to_s3.py
├── lib/
│   ├── aws-handson-stack.ts
│   └── constructs/
│       ├── api-gateway.ts
│       ├── kinesis-stream.ts
│       ├── lambda-function.ts
│       ├── roles.ts
│       └── s3-bucket.ts
├── node_modules/
├── policies/
│   ├── read-from-kinesis.json
│   ├── read-write-s3-policy.json
│   ├── write-read-s3.json
│   └── write-to-kinesis.json
├── test/
├── venv/
├── .gitignore
├── .npmignore
├── cdk.json
├── jest.config.js
├── package-lock.json
├── package.json
├── README.md
├── requirements.txt
└── tsconfig.json
```

## 19/11/2024
- Structrue based on motivation to create modular approach
- subdivided content according to file
- in lib path, I put resoruces creation into reusable construct

```
cdk-github-action
├── .github/
│   └── workflows/
│       └── deploy.yml
├── bin/
│   └── cdk-github-action.ts
├── client/
│   └── test-api-gateway.py
├── data/
│   └── TestSample.csv
├── lambda/
│   ├── api_gateway_to_kinesis.py
│   └── kinesis_to_s3.py
├── lib/
│   ├── aws-handson-stack.ts
│   └── constructs/
│       ├── api-gateway.ts
│       ├── kinesis-stream.ts
│       ├── lambda-function.ts
│       ├── roles.ts
│       └── s3-bucket.ts
├── node_modules/
├── policies/
│   ├── read-from-kinesis.json
│   ├── read-write-s3-policy.json
│   ├── write-read-s3.json
│   └── write-to-kinesis.json
├── test/
├── venv/
├── .gitignore
├── .npmignore
├── cdk.json
├── jest.config.js
├── package-lock.json
├── package.json
├── README.md
├── requirements.txt
└── tsconfig.json
```
## 18/11/2024
- Initial Project Structrue based on cdk project template
- I added two subfolder roles and policies in attempt to create modular code
- I also add github workflow to play around its usage 

```
cdk-github-action/
├── cdk.json               # CDK configuration
├── package.json           # Node.js dependencies
├── bin/
│   └── cdk-github-action.ts
├── lib/
│   ├── stack.ts       # Development stack definition
│   ├── roles/
│       ├── create-roles.ts # Script to create custom roles
│   └── policies/
│       ├── read-write-s3-policy.json
├── .github/
│   ├── workflows/
│       ├── deploy.yml     # GitHub Actions workflow
└── README.md
```