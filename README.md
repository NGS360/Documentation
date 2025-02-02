# Documentation

Goal: Provide an open-source ecosystem to enable NGS data management and analysis capabilities

## Components

Each component provide a unique/primary service

### REST Server (and database)

Provides access to database, actions, etc.
```
Endpoints:
  /projects
  /project
  /samples
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
ngs list-projects

/project:
ngs create-project
ngs describe-project
ngs delete-project
ngs modify-project
ngs find-project

/samples:
ngs list-samples
ngs add-samples
ngs describe-sample

/files:
ngs list-files  - List files in a project
ngs download-file - Download file to local location 
ngs upload-file - Upload file from local location
ngs copy-file - Copy file from remote-remote

/users:
ngs list-users

/user:
ngs describe-user

/workflows:
ngs list-workflows

/workflow:
ngs register-workflow <platform> <workflow file> - This returns a NGS360 DB id of the workflow
ngs describe-workflow <workflow-id>
ngs execute-workflow <workflow id> <input yaml> - Return an execution id
ngs cancel-workflow <execution-id>

```

### Front-End Application 

Provides user with GUI interface to application

### GA4GH WES API to AWS Batch

### GA4GH WES API to AWS Omics

### GA4GH WES API to Nextflow
