# Documentation

Goal: Provide an open-source ecosystem to enable NGS data management and analysis capabilities

## Components

Each component provide a unique/primary service

### REST Server (and database)

Provides access to database, actions, etc.

Endpoints:
  /projects
  /samples
  /files
  /users
  /user
  /workflows
  /analysis



### CLI

Provides a basic CLI interface (ngs or ngs360) to the REST server in place of using the Front-End GUI

ngs register-workflow <platform> <workflow file> - This returns a NGS360 DB id of the workflow
ngs run-workflow <workflow id> <input yaml>

### Front-End Application 

Provides user with GUI interface to application

### GA4GH WES API to AWS Batch

### GA4GH WES API to AWS Omics
