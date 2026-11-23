# AWS DevOps CI Pipeline Project

## Project Overview

This project demonstrates the implementation of an automated Continuous Integration (CI) pipeline using Amazon Web Services (AWS).

The pipeline integrates AWS CodeCommit, AWS CodeBuild, AWS CodePipeline, and Amazon S3 to automate source code retrieval, building, and artifact storage.

## Technologies Used

- AWS CodeCommit — Source code management
- AWS CodeBuild — Automated build execution
- AWS CodePipeline — CI pipeline orchestration
- Amazon S3 — Artifact storage
- AWS IAM — Access and permissions management
- Python — Application development

## Pipeline Configuration

**Pipeline Name:** PythonDevOpsPipeline

**AWS Region:** eu-north-1 (Europe, Stockholm)

### Source Stage

The pipeline retrieves application source code from AWS CodeCommit.

Status: Succeeded

### Build Stage

AWS CodeBuild executes the configured build process.

Status: Succeeded

### Artifact Storage

Build artifacts are stored in an Amazon S3 bucket under:

`PythonDevOpsPipeline/BuildArtif/`

Three build artifact objects were observed in the S3 console.

## IAM Roles and Security

AWS IAM provides permissions for the services involved in the pipeline.

The project uses service permissions to support source retrieval, build execution, and artifact storage.

**IAM role names and attached permissions:** To be documented after checking the IAM console.

## Environment Variables

The CodeBuild environment-variable configuration should be recorded here.

**Variables configured:** To be verified in AWS CodeBuild.

Do not include passwords, access keys, or secret values in this document.

## Pipeline Validation

The AWS CodePipeline console confirmed successful execution of both stages:

- Source: Succeeded
- Build: Succeeded

The S3 console also confirmed the presence of build artifact objects.

## Evidence

Screenshots collected for the project:

1. AWS CodePipeline showing successful Source and Build stages.
2. Amazon S3 showing the BuildArtif folder and generated artifact objects.

## Conclusion

This project demonstrates how AWS managed DevOps services can automate source retrieval and build execution while storing generated artifacts in Amazon S3.

The successful pipeline execution provides evidence of a functioning CI workflow.
