# React deployment pipeline with AWS CodePipeline and AWS CodeBuild

## Also can use custom domain, SSL and CloudFront distribution

This is a deployment pipeline for react apps. 
It allows you to connect to an existing github account and use
AWS CodePipeline and AWS CodeBuild to deploy your code to an S3 static website.
The pipeline will react to any push to your selected github project and branch and will deploy 
the app to the static bucket. Optionally you can use the more advanced
template to also provision a custom domain, a CloudFront distribution
and an SSL certificate for your app. 

Of course you can adapt this pipeline to work with other javascript frameworks or even simple static websites.

What you will find here:

- two cloudformation templates (directory: _cfn-templates_) :
    -   **reactToS3v3_noCloudFront.yaml** - this will deploy a simple stack with CodePipeline, CodeBuild and two S3 buckets with appropriate permissions
    -   **reactToS3v2.yaml** - additionally to the first template this one also provisions a CloudFront distribution, a custom domain and an SSL certificate

If you create the stacks with CloudFormation the two files above are the only things you need. Obviously you need to use only one of them depending on which solution you want to deploy (with or without advanced features)

## The files below are only needed if you create the pipeline manually (no CloudFormation)  
  
- bucket policy (directory: _bucket-policy_):
    - **deploy-bucket-policy.json** - if you want to configure this pipeline manually this is the bucket policy for your deploy bucket. Please replace the bucket ARN with your own bucket ARN.
    
- codebuild build commands (directory: _codebuild-build-commands_):
    - **buildspec.yaml** - these are the build commands you need to add to the codebuild project if you configure the pipeline manually
    
- role policies (directory: _role-policies_):
    - **codebuild_role.json** - this is the policy for the codebuild role if you want to configure the pipeline manually. Replace the pipeline and deploy bucket ARN's with your own.
    - **codepipeline_role.json** - this is the policy for the codepipeline role if you want to configure the pipeline manually. Replace the pipeline and deploy bucket ARN's with your own.
  
## Help & Tutorials

### Article on Majestic.cloud
[React continuous deployment pipeline from Github to S3 with AWS CodePipeline and AWS CodeBuild](https://majestic.cloud/react-continuous-deployments-from-github-to-s3/)

### CloudFormation templates
Find a more detailed description of the CloudFormation templates here:

- [Advanced template (with CloudFront, SSL, custom domain name)](https://majestic.cloud/cfntemplate/advanced-react-continuous-deployment-pipeline-from-github-to-s3-with-aws-codepipeline-and-aws-codebuild/)
- [Simple template (just S3 static site)](https://majestic.cloud/cfntemplate/react-continuous-deployment-pipeline-from-github-to-s3-with-aws-codepipeline-and-aws-codebuild/)

### Video on Youtube
This will provide you step by step guidance to setup the pipeline
[Continuous deployments from Github to S3 - Example with React](https://youtu.be/5MMSBgaERyc)
