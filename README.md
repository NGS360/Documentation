# Documentation

Goal: Provide an open-source ecosystem to enable NGS data management and analysis capabilities

## Components

We will follow the MVC design pattern: 

Model: Database Model
View: WebApp or CLI
Controller: REST API Service

### REST API Endpoints

```
/projects
  GET: List projects
  POST: Create a project

/projects/<project>:
  GET: Describe a project
  PUT: Modify/Update a project
  DELETE: Delete a project

/projects/<project>/samples:
  GET: List project samples
  POST: Add a sample

/projects/<project>/samples/<sample>:
  GET: Describe a sample
  PUT: Modify/Update a sample

/files
/users
/user
/workflows
/workflow
```

### CLI

Provides a basic CLI interface (ngs or ngs360) to the REST server in place of using the Front-End GUI

```
/projects:
ngs list-projects    (GET /projects)
ngs create-project   (POST /projects)

/projects/<project>:
ngs describe-project (GET /projects/<project>)
ngs modify-project   (PUT /projects/<project>)
ngs delete-project   (DELETE /projects/<project>)

/projects/<project>/samples:
ngs list-project-samples (GET /projects/<project>/samples)
ngs add-sample (POST /projects/<project>/samples)

/projects/<project>/samples/<sample>:
ngs describe-sample (GET /projects/<project>/samples/<sample>)
ngs modify-sample (PUT /projects/<project>/samples/<sample>)

/files:
ngs list-files  - List files in a project
ngs download-file - Download file to local location 
ngs upload-file - Upload file from local location
ngs copy-file - Copy file from remote-remote

/users:
ngs list-users (GET /users)

/users/<user>:
ngs describe-user (GET /users/<user>)

/workflows:
ngs list-workflows (GET /workflows)
ngs register-workflow (POST /workflows) - This returns a NGS360 DB id of the workflow

/workflows/<workflow>:
ngs describe-workflow (GET /workflows/<workflow>)
ngs execute-workflow (POST /workflows/<workflow>) - Return an execution id
ngs cancel-workflow (DELETE /workflows/<workflow>) 

```

### Front-End Application 

Provides user with GUI interface to application

### GA4GH WES API to AWS Batch

### GA4GH WES API to AWS Omics

### GA4GH WES API to Nextflow
