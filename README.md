AWS DevOps CI Pipeline — Python Project

Project Overview

This project implements a Continuous Integration (CI) pipeline using Amazon Web Services (AWS). It integrates AWS CodeCommit, AWS CodeBuild and AWS CodePipeline to automate the process of retrieving source code, executing Python unit tests and preparing build artifacts.

AWS Services Used

AWS CodeCommit: Stores and manages the Python application's source code.

AWS CodeBuild: Executes the build instructions defined in buildspec.yml.

AWS CodePipeline: Orchestrates the source and build stages.

AWS IAM: Manages service roles and access permissions.

Amazon CloudWatch: Records build execution logs.

Amazon S3: Stores pipeline artifacts.

Repository Structure

PythonDevOpsRepo/
├── app.py
├── test_app.py
└── buildspec.yml

IAM Roles

1. PythonDevOpsCodeBuildRole

Trusted service: codebuild.amazonaws.com

Purpose: Allows AWS CodeBuild to access the source repository, execute the build and publish logs.

The build execution permissions include access to the CodeCommit repository and the relevant CloudWatch Logs resources. S3 artifact permissions should be verified against the final pipeline configuration.

2. PythonDevOpsCodePipelineRole

Trusted service: codepipeline.amazonaws.com

Purpose: Allows AWS CodePipeline to retrieve source code, invoke AWS CodeBuild and manage pipeline artifacts stored in S3.

Build Environment

AWS Region: eu-north-1

Build project: PythonDevOpsBuild

Build image: aws/codebuild/standard:8.0

Runtime: Python 3.12

Build specification: buildspec.yml

Privileged mode: Disabled

No custom environment variables were required for the Python application. AWS CodeBuild automatically provides system environment variables during execution.

Build and Testing

The buildspec.yml file instructs CodeBuild to execute the Python unit tests using:

python -m unittest discover -v

The build also copies app.py into an output directory for artifact packaging.

Results

The initial standalone AWS CodeBuild execution completed successfully, with one unit test passing.

AWS CodePipeline was subsequently created with two stages:

Source — AWS CodeCommit

Build — AWS CodeBuild

Both stages completed successfully. A subsequent execution also processed an updated version of app.py and completed successfully.

Conclusion

The project demonstrates a functioning AWS Continuous Integration pipeline. Source code is retrieved from a managed repository, tested in a managed build environment and processed through AWS CodePipeline.

The implementation reduces manual build and testing effort and provides a foundation for future deployment automation.
