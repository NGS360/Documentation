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
ngs list-projects (GET /projects)
ngs create-project (POST /projects)

/projects/<project>:
ngs describe-project (GET /projects/<project>)
ngs delete-project (DELETE /projects/<project>)
ngs modify-project (PUT /projects/<project>)

/samples:
ngs list-samples (GET /samples)
ngs add-samples (POST /samples)

/samples/<sample>:
ngs describe-sample (GET /samples/<sample>)

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
