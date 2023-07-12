# Bootstrapping an AWS SAM Pipeline

You've probably been sent here from my blog article on getting started with SAM.  

The below is example output of bootstrapping a sam pipeline. 

``` bash
❯ sam pipeline init --bootstrap

sam pipeline init generates a pipeline configuration file that your CI/CD system
can use to deploy serverless applications using AWS SAM.
We will guide you through the process to bootstrap resources for each stage,
then walk through the details necessary for creating the pipeline config file.

Please ensure you are in the root folder of your SAM application before you begin.

Select a pipeline template to get started:
	1 - AWS Quick Start Pipeline Templates
	2 - Custom Pipeline Template Location
Choice: 1

Cloning from https://github.com/aws/aws-sam-cli-pipeline-init-templates.git (process may
take a moment)
Select CI/CD system
	1 - Jenkins
	2 - GitLab CI/CD
	3 - GitHub Actions
	4 - Bitbucket Pipelines
	5 - AWS CodePipeline
Choice: 5
Which pipeline template would you like to use?
	1 - Two-stage pipeline
	2 - Two-stage pipeline with monorepo
Choice []: 1
You are using the 2-stage pipeline template.
 _________    _________
|         |  |         |
| Stage 1 |->| Stage 2 |
|_________|  |_________|

Checking for existing stages...

[!] None detected in this account.

Do you want to go through stage setup process now? If you choose no, you can still reference other bootstrapped resources. [Y/n]: y

For each stage, we will ask for [1] stage definition, [2] account details, and [3]
reference application build resources in order to bootstrap these pipeline
resources.

We recommend using an individual AWS account profiles for each stage in your
pipeline. You can set these profiles up using aws configure or ~/.aws/credentials. See
[https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-set-up-credentials.html].


Stage 1 Setup

[1] Stage definition
Enter a configuration name for this stage. This will be referenced later when you use the sam pipeline init command:
Stage configuration name: dev

[2] Account details
The following AWS credential sources are available to use.
To know more about configuration AWS credentials, visit the link below:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html
	1 - Environment variables
	q - Quit and configure AWS credentials
Select a credential source to associate with this stage: 1
Associated account 123456789012 with configuration dev.

Enter the region in which you want these resources to be created [us-east-1]: ap-southeast-2
Enter the pipeline IAM user ARN if you have previously created one, or we will create one for you []:

[3] Reference application build resources
Enter the pipeline execution role ARN if you have previously created one, or we will create one for you []:
Enter the CloudFormation execution role ARN if you have previously created one, or we will create one for you []:
Please enter the artifact bucket ARN for your Lambda function. If you do not have a bucket, we will create one for you []:
Does your application contain any IMAGE type Lambda functions? [y/N]:

[4] Summary
Below is the summary of the answers:
	1 - Account: 123456789012
	2 - Stage configuration name: dev
	3 - Region: ap-southeast-2
	4 - Pipeline user: [to be created]
	5 - Pipeline execution role: [to be created]
	6 - CloudFormation execution role: [to be created]
	7 - Artifacts bucket: [to be created]
	8 - ECR image repository: [skipped]
Press enter to confirm the values above, or select an item to edit the value:

This will create the following required resources for the 'dev' configuration:
	- Pipeline IAM user
	- Pipeline execution role
	- CloudFormation execution role
	- Artifact bucket
Should we proceed with the creation? [y/N]: y
	Creating the required resources...
	Successfully created!
The following resources were created in your account:
	- Pipeline execution role
	- CloudFormation execution role
	- Artifact bucket
	- Pipeline IAM user
Pipeline IAM user credential:
	AWS_ACCESS_KEY_ID: AKIAZRMEXAMPLE3FF7NZ
	AWS_SECRET_ACCESS_KEY: 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
View the definition in .aws-sam/pipeline/pipelineconfig.toml,
run sam pipeline bootstrap to generate another set of resources, or proceed to
sam pipeline init to create your pipeline configuration file.

Before running sam pipeline init, we recommend first setting up AWS credentials
in your CI/CD account. Read more about how to do so with your provider in
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-generating-example-ci-cd-others.html.

Checking for existing stages...

Only 1 stage(s) were detected, fewer than what the template requires: 2. If these are incorrect, delete .aws-sam/pipeline/pipelineconfig.toml and rerun

Do you want to go through stage setup process now? If you choose no, you can still reference other bootstrapped resources. [Y/n]: y

For each stage, we will ask for [1] stage definition, [2] account details, and [3]
reference application build resources in order to bootstrap these pipeline
resources.

We recommend using an individual AWS account profiles for each stage in your
pipeline. You can set these profiles up using aws configure or ~/.aws/credentials. See
[https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-set-up-credentials.html].


Stage 2 Setup

[1] Stage definition
Enter a configuration name for this stage. This will be referenced later when you use the sam pipeline init command:
Stage configuration name: prod

[2] Account details
The following AWS credential sources are available to use.
To know more about configuration AWS credentials, visit the link below:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html
	1 - Environment variables
	q - Quit and configure AWS credentials
Select a credential source to associate with this stage: 1
Associated account 123456789012 with configuration prod.

Enter the region in which you want these resources to be created [us-east-1]: ap-southeast-2
Pipeline IAM user ARN: arn:aws:iam::123456789012:user/aws-sam-cli-managed-dev-pipeline-reso-PipelineUser-4JN0X9ZLGVNP

[3] Reference application build resources
Enter the pipeline execution role ARN if you have previously created one, or we will create one for you []:
Enter the CloudFormation execution role ARN if you have previously created one, or we will create one for you []:
Please enter the artifact bucket ARN for your Lambda function. If you do not have a bucket, we will create one for you []:
Does your application contain any IMAGE type Lambda functions? [y/N]:

[4] Summary
Below is the summary of the answers:
	1 - Account: 123456789012
	2 - Stage configuration name: prod
	3 - Region: ap-southeast-2
	4 - Pipeline user ARN: arn:aws:iam::123456789012:user/aws-sam-cli-managed-dev-pipeline-reso-PipelineUser-4JN0X9ZLGVNP
	5 - Pipeline execution role: [to be created]
	6 - CloudFormation execution role: [to be created]
	7 - Artifacts bucket: [to be created]
	8 - ECR image repository: [skipped]
Press enter to confirm the values above, or select an item to edit the value:

This will create the following required resources for the 'prod' configuration:
	- Pipeline execution role
	- CloudFormation execution role
	- Artifact bucket
Should we proceed with the creation? [y/N]: y
	Creating the required resources...
	Successfully created!
The following resources were created in your account:
	- Pipeline execution role
	- CloudFormation execution role
	- Artifact bucket
View the definition in .aws-sam/pipeline/pipelineconfig.toml,
run sam pipeline bootstrap to generate another set of resources, or proceed to
sam pipeline init to create your pipeline configuration file.

Checking for existing stages...

2 stage(s) were detected, matching the template requirements. If these are incorrect, delete .aws-sam/pipeline/pipelineconfig.toml and rerun
What is the Git provider?
	1 - Bitbucket
	2 - CodeCommit
	3 - GitHub
	4 - GitHubEnterpriseServer
Choice []: 3
What is the full repository id (Example: some-user/my-repo)?: dbla-tech/demo-hello-world
What is the Git branch used for production deployments? [main]:
What is the template file path? [template.yaml]:
We use the stage configuration name to automatically retrieve the bootstrapped resources created when you ran `sam pipeline bootstrap`.

Here are the stage configuration names detected in .aws-sam/pipeline/pipelineconfig.toml:
	1 - dev
	2 - prod
Select an index or enter the stage 1's configuration name (as provided during the bootstrapping): 1
What is the sam application stack name for stage 1? [sam-app]: dev-hello-world
Stage 1 configured successfully, configuring stage 2.

Here are the stage configuration names detected in .aws-sam/pipeline/pipelineconfig.toml:
	1 - dev
	2 - prod
Select an index or enter the stage 2's configuration name (as provided during the bootstrapping): 2
What is the sam application stack name for stage 2? [sam-app]: prd-hello-world
Stage 2 configured successfully.

To deploy this template and connect to the main git branch, run this against the leading account:
`sam deploy -t codepipeline.yaml --stack-name <stack-name> --capabilities=CAPABILITY_IAM`.
SUMMARY
We will generate a pipeline config file based on the following information:
	What is the Git provider?: GitHub
	What is the full repository id (Example: some-user/my-repo)?: dbla-tech/demo-hello-world
	What is the Git branch used for production deployments?: main
	What is the template file path?: template.yaml
	Select an index or enter the stage 1's configuration name (as provided during the bootstrapping): 1
	What is the sam application stack name for stage 1?: dev-hello-world
	What is the pipeline execution role ARN for stage 1?: arn:aws:iam::123456789012:role/aws-sam-cli-managed-dev-pipe-PipelineExecutionRole-7I8C8GX3GOH0
	What is the CloudFormation execution role ARN for stage 1?: arn:aws:iam::123456789012:role/aws-sam-cli-managed-dev-p-CloudFormationExecutionR-1A03VMK0VKM4B
	What is the S3 bucket name for artifacts for stage 1?: aws-sam-cli-managed-dev-pipeline-artifactsbucket-1u3pfrhiab4v4
	What is the ECR repository URI for stage 1?:
	What is the AWS region for stage 1?: ap-southeast-2
	Select an index or enter the stage 2's configuration name (as provided during the bootstrapping): 2
	What is the sam application stack name for stage 2?: prd-hello-world
	What is the pipeline execution role ARN for stage 2?: arn:aws:iam::123456789012:role/aws-sam-cli-managed-prod-pip-PipelineExecutionRole-GZKNLQHOXEPG
	What is the CloudFormation execution role ARN for stage 2?: arn:aws:iam::123456789012:role/aws-sam-cli-managed-prod-CloudFormationExecutionR-6A6WWC0ZNDWL
	What is the S3 bucket name for artifacts for stage 2?: aws-sam-cli-managed-prod-pipeline-artifactsbucket-xe16meha2hde
	What is the ECR repository URI for stage 2?:
	What is the AWS region for stage 2?: ap-southeast-2
Successfully created the pipeline configuration file(s):
	- codepipeline.yaml
	- assume-role.sh
	- pipeline/buildspec_unit_test.yml
	- pipeline/buildspec_build_package.yml
	- pipeline/buildspec_integration_test.yml
	- pipeline/buildspec_feature.yml
	- pipeline/buildspec_deploy.yml
```