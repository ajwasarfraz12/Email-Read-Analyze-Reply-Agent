# System Architecture

The Email Read, Analyze & Reply AI Agent consists of multiple connected automation components.

## Architecture

```mermaid
flowchart TD
    A[" Schedule Trigger"] --> B[" Gmail<br/>Get All Messages"]
    B --> C[" Gmail<br/>Get Message Details"]
    C --> D[" AI Agent"]
    D --> F[" Airtable<br/>Store Email & Reply"]
    F --> G[" Gmail<br/>Mark Message as Read"]
    
    E[" Google Gemini<br/>Chat Model"] -. "Powers" .-> D

    A:::trigger
    B:::gmail
    C:::gmail
    D:::agent
    E:::ai
    F:::database
    G:::success

    classDef trigger fill:#E8F1FF,stroke:#4285F4,stroke-width:2px,color:#111
    classDef gmail fill:#FFF3E6,stroke:#EA4335,stroke-width:2px,color:#111
    classDef agent fill:#F3E8FF,stroke:#8E44AD,stroke-width:2px,color:#111
    classDef ai fill:#E8F8F0,stroke:#34A853,stroke-width:2px,color:#111
    classDef database fill:#FFF8E1,stroke:#F4B400,stroke-width:2px,color:#111
    classDef success fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,color:#111
```

## Data Flow

1. The schedule trigger starts the workflow.
2. Gmail messages are retrieved.
3. Detailed message information is collected.
4. The AI Agent processes the email.
5. Google Gemini generates the AI response.
6. The email information and reply are stored in Airtable.
7. The processed Gmail message is marked as read.
