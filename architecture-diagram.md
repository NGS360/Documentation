# Architecture Diagram

This document contains an architecture diagram for the project using Mermaid syntax. You can view this diagram in any Markdown viewer that supports Mermaid (like GitHub, VS Code with the Mermaid extension, or online Mermaid editors).

## System Architecture

```mermaid
graph TD
    %% Client Layer
    subgraph "Client Layer"
        WebClient[Web Client]
        CommandLineClient[CommandLine Client]
    end

    %% API Gateway Layer
    subgraph "API Gateway Layer"
        RESTAPIService[Rest API Service]
        GA4GHWESAPIService[GA4GH WES API Service]
    end

    %% Application Layer
    subgraph "Application Layer"
        RESTAPIWorker[REST API Worker]
        GA4GHWESDaemon[GA4GH WES Daemon]
    end

    %% Data Layer
    subgraph "Data Layer"
        PrimaryDB[(Primary Database)]
        OpenSearch[(Open Search)]
    end

    %% External Services
    subgraph "External Services"
        Arvados[Arvados]
        SevenBridges[SevenBridges]
        AWSOmics[AWS Omics]
    end

    %% Connections
    WebClient --> RESTAPIService
    CommandLineClient --> RESTAPIService
    WebClient --> GA4GHWESAPIService

    RESTAPIService --> RESTAPIWorker
    GA4GHWESAPIService --> GA4GHWESDaemon

    RESTAPIService --> PrimaryDB
    RESTAPIWorker --> PrimaryDB
    GA4GHWESDaemon --> PrimaryDB
    RESTAPIWorker --> OpenSearch

    GA4GHWESDaemon --> Arvados
    GA4GHWESDaemon --> SevenBridges
    GA4GHWESDaemon --> AWSOmics

```

## Component Details

### Client Layer
- **Web Client**: Browser-based interface for users
- **Mobile Client**: Native mobile applications (iOS/Android)
- **Third-Party Client**: External systems integrating with our API

### API Gateway Layer
- **API Gateway**: Central entry point for all client requests
- **Authentication Service**: Handles user authentication and authorization
- **Rate Limiting**: Controls request frequency to prevent abuse

### Application Layer
- **Service A**: [Describe main functionality]
- **Service B**: [Describe main functionality]
- **Service C**: [Describe main functionality]

### Data Layer
- **Primary Database**: Main data storage (e.g., PostgreSQL, MongoDB)
- **Cache System**: Fast access temporary storage (e.g., Redis)
- **File Storage**: Storage for documents, images, etc. (e.g., S3)

### External Services
- **Payment Provider**: Handles payment processing
- **Email Service**: Manages email communications
- **Analytics Service**: Collects and processes usage data

## Alternative Architecture Views

### Deployment View

```mermaid
flowchart TD
    subgraph "Cloud Provider"
        subgraph "Region 1 (Primary)"
            WebServer1[Web Server]
            AppServer1[App Server]
            Database1[(Database)]
            Cache1[(Cache)]
        end
        
        subgraph "Region 2 (Backup)"
            WebServer2[Web Server]
            AppServer2[App Server]
            Database2[(Database)]
            Cache2[(Cache)]
        end
        
        LoadBalancer[Load Balancer]
        CDN[Content Delivery Network]
        
        LoadBalancer --> WebServer1
        LoadBalancer --> WebServer2
        
        WebServer1 --> AppServer1
        WebServer2 --> AppServer2
        
        AppServer1 --> Database1
        AppServer1 --> Cache1
        
        AppServer2 --> Database2
        AppServer2 --> Cache2
        
        Database1 <--> Database2
    end
    
    Users[Users] --> CDN
    Users --> LoadBalancer
    CDN --> WebServer1
    CDN --> WebServer2
```

### Security View

```mermaid
flowchart TD
    Internet((Internet)) --> Firewall
    
    subgraph "Security Layers"
        Firewall --> WAF[Web Application Firewall]
        WAF --> LoadBalancer[Load Balancer]
        LoadBalancer --> DMZ[DMZ Network]
        DMZ --> InternalFirewall[Internal Firewall]
        InternalFirewall --> PrivateNetwork[Private Network]
    end
    
    subgraph "DMZ Network"
        WebServers[Web Servers]
        APIGateway[API Gateway]
    end
    
    subgraph "Private Network"
        AppServers[Application Servers]
        Databases[(Databases)]
        InternalServices[Internal Services]
    end
    
    DMZ --> WebServers
    DMZ --> APIGateway
    PrivateNetwork --> AppServers
    PrivateNetwork --> Databases
    PrivateNetwork --> InternalServices
```

## How to Customize This Diagram

1. Replace the placeholder components with your actual system components
2. Adjust the relationships between components to match your architecture
3. Add or remove components as needed
4. Update the component descriptions with specific details about your system
5. Consider adding additional views (e.g., data flow, sequence diagrams) as needed

You can edit this Mermaid diagram using any text editor, and preview it using:
- VS Code with the Mermaid extension
- GitHub (which natively supports Mermaid)
- Online Mermaid editor: https://mermaid.live/
