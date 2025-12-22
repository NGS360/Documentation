# Use Case Document

## Project Overview

NGS360 is an open-source enterprise-scale NGS data and analysis platform.

NGS360 provides a centralized platform for an organization to manage NGS data and run analytical pipelines using their backend engine of choice.

Users can innteract with NGS360 either through the GUI or CLI, both of which uses the underlying REST API.
Users can create and search for projects, samples, run analytical workflows on samples.
Users can ingest data from sequencers, vendors, external reposititories.

## Actors
[List and describe the primary users/roles who will interact with the system]

- **Actor 1**: [Description of role and responsibilities]
- **Actor 2**: [Description of role and responsibilities]
- **Actor 3**: [Description of role and responsibilities]

## Use Cases

### Use Case 1: Search for a project

**ID**: UC-001  
**Primary Actor**: [Actor who initiates this use case]  
**Description**: Users can search for a project using the Google-like search inferface on the home page (or by the API endpoint /search). Projects matching the search criteria will be displayed to the user in table of search results where they can navigate to their project of interest.

**Preconditions**:
- [Condition that must be true before the use case begins]
- [Another precondition if applicable]

**Main Flow**:
1. [First step of the use case]
2. [Second step of the use case]
3. [Third step of the use case]
4. [Continue with additional steps as needed]

**Alternative Flows**:
- **A1**: [Description of alternative scenario]
  1. [Step 1 of alternative flow]
  2. [Step 2 of alternative flow]
  3. [Continue as needed]

**Postconditions**:
- [Condition that must be true when the use case completes successfully]
- [Another postcondition if applicable]

### Use Case 2: Create a project

**ID**: UC-002  
**Primary Actor**: [Actor who initiates this use case]  
**Description**: Users can create a project from the web UI or by using the API.  The project will be added to the NGS360 database and indexed by OpenSearch.

**Preconditions**:
- [Condition that must be true before the use case begins]
- [Another precondition if applicable]

**Main Flow**:
1. [First step of the use case]
2. [Second step of the use case]
3. [Third step of the use case]
4. [Continue with additional steps as needed]

**Alternative Flows**:
- **A1**: [Description of alternative scenario]
  1. [Step 1 of alternative flow]
  2. [Step 2 of alternative flow]
  3. [Continue as needed]

**Postconditions**:
- [Condition that must be true when the use case completes successfully]
- [Another postcondition if applicable]

### Use Case 3: View a project

**ID**: UC-003  
**Primary Actor**: [Actor who initiates this use case]  
**Description**: Users will be able to view a project page containing all relevant summary information about a project including project information, sample information, analysis performed on samples in the project.

**Preconditions**:
- [Condition that must be true before the use case begins]
- [Another precondition if applicable]

**Main Flow**:
1. [First step of the use case]
2. [Second step of the use case]
3. [Third step of the use case]
4. [Continue with additional steps as needed]

**Alternative Flows**:
- **A1**: [Description of alternative scenario]
  1. [Step 1 of alternative flow]
  2. [Step 2 of alternative flow]
  3. [Continue as needed]

**Postconditions**:
- [Condition that must be true when the use case completes successfully]
- [Another postcondition if applicable]

### Use Case 4: Register & Run a workflow

A user will POST a workflow to /workflow to register the workflow with NGS360.  The POST request will specify what backend engine the workflow is targetted for.  A NGS360 workflow id will be returned to the user.

The user will then POST run requests to /runs using the NGS360 workflow id.

A backend daemon will submit the run request to the engine on behalf of the user.

This approach will allow all user-engine interactions to go exclusively through NGS360 such that the user will not need to know any details about the underlying engine used.

AWS HealthOmics as an example:

1. User posts a workflow specifying AWS Omics as the engine
2. NGS360 adds the workflow to Omics, adds the workflow to its database then returns a NGS360 workflow id.
3. Users can then submit workflow execution via GA4GH WES API using the NGS360 workflow id.

AWS Batch as an example:

1. User posts a workflow specifying AWS Batch as the engine
2. NGS360 adds the workflow to its database then returns a NGS360 workflow id.
3. Users can then submit workflow execution via GA4GH WES API using the NGS360 workflow id.

Pros:

1. NGS360 is completely disconnected from Omics hence back-end can change at any time
2. Every workflow run is loged through NGS360
3. Users don't need AWS console access
4. This supports enabling other engines such as AWS Batch where a workflow won't have its own id.

Cons:

1. Added overhead on NGS360 to have daemon supporting Omics, Batch and other engines

## Non-Functional Requirements

### Performance
- [Specify response time requirements]
- [Specify throughput requirements]
- [Specify other performance metrics]

### Security
- [Specify authentication requirements]
- [Specify authorization requirements]
- [Specify data protection requirements]

### Usability
- [Specify ease-of-use requirements]
- [Specify accessibility requirements]
- [Specify user interface requirements]

### Reliability
- [Specify availability requirements]
- [Specify fault tolerance requirements]
- [Specify recovery requirements]

## Glossary
- **Term 1**: [Definition]
- **Term 2**: [Definition]
- **Term 3**: [Definition]

## Appendices
[Include any additional information, diagrams, or references that support the use cases]