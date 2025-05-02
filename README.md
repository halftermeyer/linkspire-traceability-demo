# linkspire-traceability-demo
A Neo4j-powered demo of Linkspire’s 5G router traceability platform, integrating SFDC, Doors, Pront, and Quality Centres. Features graph queries to trace requirements, designs, and test cases.

## Introduction
- **Pitch**: "Welcome to the Linkspire 5G Router Traceability Platform, powered by Neo4j! Today, I’ll show how our graph technology connects Linkspire’s data—SFDC, Doors, Pront, and Quality Centres—to track every requirement, design, and test in real time. We’ll uncover bottlenecks like a failed band-switching test and maybe a quirky quantum surprise hidden deep in the system. Let’s make complexity clear!"

## Step 1: The Challenge
- **Context**: Linkspire, a telecom innovator, builds 5G routers but struggles with siloed data across four tools:
  - *SFDC*: Customer requests (e.g., `CR001` for 10Gbps throughput).
  - *Doors*: Engineering requirements.
  - *Pront*: Design specs.
  - *Quality Centres*: Test results.
- **Problem**: Teams can’t easily trace how a customer need becomes a tested product or spot issues like a failed test.

## Step 2: Data Federation 
- **Solution**: Linkspire has federated the data:
  - Uses eqube connectors to pull from SFDC, Doors, Pront, and Quality Centres.
  - Maps fields (e.g., SFDC’s request ID to Doors’ requirement ID) without replication.
  - Ships linked data to Neo4j as nodes (`CustomerRequest`, `Requirement`, `Design`, `TestCase`) and relationships (`SATISFIES`, `IMPLEMENTED_BY`, `TESTED_BY`, `DEPENDS_ON`).


## Step 3: Neo4j’s Graph Power in Query [**Demo Queries**](./linkspire_demo_queries.csv)
- **Setup**: from any Neo4j empty database + UPX 
- play queries
  1. Ingest graph 
  2. Create Full-Text composite index for future Bloom queries:
  3. Show model
  4. Show a SFDC customer request and interact with the view
  5. Show upstream dependencies from a SFDC customer request (via Doors requirements, Pront disigns and Quality Centres test cases)
  6. Root cause analysis from a SFDC customer request
  7. Impact Analysis from a Quality Centres test case
  8. Easter-egg to showcase fast traversal capabilities: adds a long chain of dependency
  9. Replay upstream dependency and root cause.


## Step 4: Exploration in Explore [**Demo Perspective**](./linkspire_perspective.json)
- Full text search: Band Switching
- present custom icons and styling
- Clear view
- Full text search: CR001
- present saved cypher in perspective
- scene actions from CR001: upstream dependency (comment rule based styling)
- scene actions from CR001: root cause
- impact analysis from a Test Case

## Conclusion
- **Takeaway**: Neo4j empowers Linkspire to connect silos, trace impacts, and find hidden issues.
