# 1. The SettleMint platform: What it is and what it does


SettleMint is a full-stack blockchain infrastructure and application development platform designed to accelerate the creation, deployment, and management of enterprise-grade decentralized applications. It streamlines blockchain adoption by combining essential infrastructure services—such as network setup, node configuration, smart contract development, middleware, off-chain integrations, and front-end deployments—into a unified environment. SettleMint supports both **public networks** (Ethereum, Polygon, Optimism, Arbitrum, and Hedera Hashgraph) and **permissioned networks** (Hyperledger Besu, Quorum, and Hyperledger Fabric), significantly reducing complexity and accelerating your time-to-market.

Acting as a Swiss Army knife for blockchain developers, SettleMint provides comprehensive, pre-configured tooling to simplify every stage of your blockchain development journey. The platform includes built-in IDEs for smart contract development, automatically generated REST and GraphQL APIs, real-time data indexing middleware, enterprise-grade integrations, and secure off-chain storage and database options. Whether deploying applications via a Managed SaaS or Self-Managed (on-premises) model, SettleMint’s integrated approach ensures robust security, seamless scalability, and simplified operational management for enterprise-grade decentralized applications.


<img width="1464" alt="image" src="https://github.com/user-attachments/assets/26e51a72-7acf-4fce-9e7c-6de50600c407" />


---

# 2. The SettleMint components and their usage

SettleMint’s platform encompasses a **comprehensive ecosystem** of services that can be configured for diverse blockchain scenarios. Below is a **high-level summary table**, followed by **detailed component descriptions** (including specifics about private permissioned networks, Layer 1 and Layer 2 public blockchains, participant management, node configuration, transaction signing, off-chain integrations, and more).

## Components Overview Table

| **Category**                           | **Component**                     | **Usage & Ecosystem Fit**                                                                                                                                            | **Docs**                                                                                              |
|----------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| **1. Blockchain Infrastructure**       | **Blockchain Network Manager**    | Launch and manage both public and private networks. Configure nodes, choose consensus mechanisms, and handle chain settings to lay the foundation of your application.                                      | [Network Management](#network-management)                                                             |
|                                        | **Consortium Manager**            | Oversee participant onboarding and permissioning in private or consortium-based blockchains, enforcing governance rules in multi-organization projects.                                                     | [Consortium Setup](#consortium-setup)                                                                 |
|                                        | **Blockchain Nodes**              | Deploy validating or non-validating nodes (EVM-based or otherwise). Validating nodes participate in consensus, while non-validating nodes manage load distribution and serve read requests.                 | [Node Management](#blockchain-nodes)                                                                  |
|                                        | **Blockchain Load Balancer**      | Distribute transaction requests across multiple nodes, improving throughput, fault tolerance, and overall network resilience.                                                                                | [Load Balancer](#load-balancer)                                                                        |
|                                        | **Transaction Signer**            | Provides a secure environment for signing transactions before they are broadcast to the network, minimizing the exposure of private keys at the application layer.                                          | [Transaction Signer](#transaction-signer)                                                             |
|                                        | **Blockchain Explorer**           | Inspect transactions, blocks, and contracts through a graphical interface or API. This is indispensable for diagnostics and confirming on-chain activity.                                                   | [Blockchain Explorer](#blockchain-explorer)                                                           |
| **2. Smart Contract Development**      | **Code Studio (IDE)**             | A web-based IDE for writing, compiling, and deploying smart contracts (e.g., in Solidity or Chaincode). It integrates with the rest of the platform for a seamless dev experience.                           | [Code Studio Guide](#code-studio-ide)                                                                 |
|                                        | **SDK CLI**                       | A command-line toolkit that supports automated workflows, including contract compilation, deployment, and versioning, all from within your terminal or CI/CD pipeline.                                      | [SDK CLI Guide](#sdk-cli)                                                                              |
| **3. Middleware & API Layer**          | **Smart Contract API Portal**     | Automatically generates REST or GraphQL endpoints for your deployed contracts, eliminating manual integration code and simplifying front-end or third-party access.                                         | [Smart Contract API Portal](#smart-contract-api-portal)                                               |
|                                        | **Graph Middleware**              | Indexes on-chain events so you can query them in real time using GraphQL. Suited for analytics, marketplace applications, or any scenario involving data-intensive queries.                                  | [Graph Middleware](#graph-middleware)                                                                  |
|                                        | **Ethereum Attestation Indexer**  | Focused on indexing attestations from the Ethereum Attestation Service (EAS), facilitating credential management, compliance checks, and advanced auditing.                                                 | [Attestation Indexer](#ethereum-attestation-indexer)                                                  |
|                                        | **Blockchain Explorer API**       | Grants programmatic access to the data shown in the Explorer, which is useful for automated monitoring, scripting, or custom analytics integrations.                                                        | [Blockchain Explorer API](#blockchain-explorer-api)                                                   |
| **4. Enterprise Integration & Automation** | **Integration Studio**            | A drag-and-drop interface for building workflows that connect on-chain events to external systems (e.g., ERP, CRM, HR). Reduces custom coding for routine integrations.                                     | [Integration Studio](#integration-studio)                                                             |
| **5. Storage & Data Management**       | **S3 Storage (MinIO)**            | An S3-compatible object storage ideal for large files and logs that don’t require on-chain immutability. Can be used for user-generated content or enterprise documents.                                     | [S3 Storage](#s3-storage-minio)                                                                        |
|                                        | **IPFS Storage**                  | Decentralized and tamper-proof file storage for documents, certificates, and other sensitive data. Ideal for publicly verifiable artifacts like NFT metadata.                                              | [IPFS Storage](#ipfs-storage)                                                                          |
|                                        | **Hasura GraphQL Engine**         | A real-time GraphQL API atop a PostgreSQL database for off-chain data. Simplifies data handling by providing instant schema-based queries and updates.                                                    | [Hasura GraphQL](#hasura-graphql-engine)                                                               |
| **6. Application Deployment & Management** | **Custom Deployments**            | Containerize and deploy both front-end and back-end components. This approach makes it straightforward to scale each component independently and roll out updates efficiently.                                | [Custom Deployments](#custom-deployments)                                                             |
| **7. Security & Authentication**       | **Private Key Management**        | Various options, from software-based storage to Hardware Security Modules (HSMs), for safeguarding cryptographic keys and ensuring secure transactions.                                                    | [Key Management](#private-key-management)                                                              |
|                                        | **Access Tokens (PAT/AAT)**       | Control access to the platform and its APIs using token-based authentication. Enables role-based permissions for both user and machine (app) identities.                                                   | [Access Tokens](#access-tokens-pataat)                                                                 |
| **8. Application Kits**               | **Asset Tokenization Kit**        | A full-stack accelerator for tokenizing assets, including prebuilt smart contracts and a ready-to-use dApp codebase to jump-start tokenization projects.                                                 | [Asset Tokenization Kit](#asset-tokenization-kit)                                                      |
---

# Platform components: detailed sescription

Below is an **in-depth** look at each major component. We have seamlessly **incorporated** the details on private permissioned networks (Hyperledger Besu, Quorum, Hyperledger Fabric), Layer 1 and Layer 2 public blockchains, participant management, node configuration, transaction signing, code development, and more. All content is retained to ensure you have the **full context** needed for enterprise blockchain projects.

## **Private Permissioned Networks**
- **Hyperledger Besu**  A blockchain usable for both public and private contexts, supporting IBFT, QBFT, and PoW consensus. Often adopted for permissioned environments needing fine-grained access controls and privacy.
- **Quorum**   A private Ethereum fork incorporating encrypted transactions and privacy features. Suitable for enterprises that want Ethereum smart contract compatibility without exposing sensitive data.
- **Hyperledger Fabric**   A modular blockchain allowing pluggable consensus. Widely used in business settings that require robust security, customizable endorsement policies, and efficient performance.

**Consortium Manager & Participant Permissions**  
In SettleMint, the **Consortium Manager** helps you manage participants for private networks. Each participant can have **granular permissions** (e.g., ability to add validating nodes, invite members, or manage governance), ensuring enterprise-class security and **decentralized decision-making**.

**Network Manager: Genesis Files & External Nodes**  
The **Network Manager** allows you to create or join external blockchain networks by configuring genesis files (defining chain parameters) and specifying bootnodes. This fosters **interoperability** and **consortium formation**, letting you align all nodes under a shared initial state while securely integrating additional participants.

## **Layer 1 (L1) Public Networks**
- **Ethereum**   A decentralized blockchain transitioning to Proof of Stake (PoS), known for its extensive developer community and smart contract capabilities.
- **Avalanche**  High-speed chain with subnet support and a PoS approach, delivering low-cost and near-instant finality.
- **Hedera Hashgraph**   A scalable public ledger offering enterprise-level security and low fees, relying on asynchronous Byzantine Fault Tolerance.

By selecting an L1 network within the **Network Manager**, you can deploy and manage nodes, handle load balancing, and integrate with SettleMint’s transaction signing, making it easier to develop or migrate dApps onto top-tier public blockchains.

## **Layer 2 (L2) Public Networks**
- **Polygon PoS**  A sidechain for Ethereum that offers faster transactions and lower fees, connected to mainnet for added security.
- **Polygon zkEVM**   A zero-knowledge rollup solution providing even greater efficiency, bundling transactions off-chain while preserving Ethereum’s security.
- **Optimism**  Uses Optimistic Rollups to group off-chain transactions into batches verified on Ethereum.
- **Arbitrum**  Another leading Optimistic Rollup-based approach to improve Ethereum’s scalability and reduce fees.

Layer 2s are favored for high-volume applications, as they ease congestion on mainnet Ethereum while retaining EVM compatibility. Through SettleMint, you can deploy or connect to these networks, benefiting from the platform’s end-to-end infrastructure and dev tooling.

## **Blockchain Nodes**
The **Nodes** panel in SettleMint’s Network Manager provides a holistic view of the network, whether it’s private or public. You can:

- **Add Validating Nodes:** Nodes that participate in consensus, securing the network.  
- **Add Non-Validating Nodes:** Handle data queries and reduce validator load.  
- **Configure Load Balancers:** Improve performance by routing requests across multiple nodes.  
- **Check Live Logs:** Monitor node statuses in real time, tracking identity, enode URLs, and configuration details.
This granular management ensures your **network remains stable** and **scalable**, even under heavy workloads.

## **Transaction Signer**
The **Transaction Signer** is a critical piece in SettleMint that securely signs and broadcasts transactions. By integrating with nodes via JSON-RPC or WebSockets, it provides:

- **Key Management Services:** Including HSM support, ensuring sensitive private keys remain protected.  
- **API Access & Audit Logging:** Allowing you to monitor transaction flows and enforce role-based control.  
- **Automated Transaction Execution:** Suitable for workflows requiring consistent, programmatic on-chain updates.

## **Blockchain Load Balancer**
To maintain **high availability** and resource efficiency, SettleMint includes a dedicated load balancer. It distributes JSON-RPC calls, GraphQL queries, and transaction submissions across multiple nodes, minimizing downtime if one node fails and preventing any single node from becoming a bottleneck. This is especially vital for enterprise-scale applications with large user bases or transaction volumes.

## **Blockchain Explorer**

The **Blockchain Explorer** offers real-time insights into:
- **Transactions:** See if they’ve been mined or validated.  
- **Blocks:** Examine block production, verifying chain integrity.  
- **Smart Contracts:** Inspect states, method calls, and event logs.  
- **Network Participants:** Track node identities and governance roles in private networks.
It relies on fast JSON-RPC and GraphQL queries, making it a cornerstone for auditing, diagnostic checks, and compliance reporting.

## **Code Studio (IDE)**
A **browser-based IDE** that streamlines contract development for various networks:

- **Foundry/Hardhat Integration:** Preconfigured setups to compile, test, and deploy Solidity contracts for EVM-based chains like Hyperledger Besu or Quorum.  
- **Chaincode Support:** For Hyperledger Fabric networks, enabling enterprise-grade business logic.  
- **Templates & Custom Libraries:** Jump-start new projects or adapt existing code easily.  
- **Terminal & GitHub Integration:** Enables collaboration, version control, and quick dependency management.
Because it’s fully hosted in SettleMint, you don’t need a local environment—resulting in a frictionless dev experience.

## **Smart Contract API Portal**
After deployment, the **Smart Contract API Portal** translates your contract ABIs into **REST** and **GraphQL** endpoints—often termed “write middleware” because they allow writing data on-chain through these automatically generated APIs. It includes:

- **OpenAPI Documentation:** So you can test endpoints directly in the browser.  
- **Interactive Interface:** Easily check function parameters and event outputs.  
- **Hundreds of Endpoints per Contract:** Eliminating the need to manually code them.
This shortens the time from contract deployment to integration with front ends or third-party services.

## **Graph Middleware**
**Graph Middleware** accelerates read operations by indexing specified on-chain data in real time. Developers define subgraphs that specify which events, transactions, and states to monitor, enabling quick data retrieval via GraphQL. Popular for:

- **DeFi Dashboards**  
- **NFT Marketplaces**  
- **Real-time Analytics**
By removing the need to scan entire blockchains manually, Graph Middleware makes complex queries simple and efficient.

## **Ethereum Attestation Indexer**
Enterprise solutions often require **verifiable credentials** (e.g., identity attestations or compliance confirmations). The **Ethereum Attestation Indexer** monitors and indexes data produced by the **Ethereum Attestation Service (EAS)**. It then presents these attestations through a GraphQL API, allowing:

- **Identity Verification**  
- **Reputation Systems**  
- **Regulatory Tracking**
This specialized middleware simplifies trust-based interactions, reducing custom code for indexing or auditing attestations.

## **Integration Studio**
The **Integration Studio** is a **low-code, Node-RED-based** environment for orchestrating cross-system workflows:

- **4,000+ Pre-Built Connectors:** Link blockchains to ERP, CRM, HR, AI/ML, and other external systems.  
- **Event-Driven Processes:** React to on-chain activities by triggering off-chain actions, such as sending emails or updating databases.  
- **API Management:** Expose blockchain functions as RESTful endpoints or incorporate external APIs into on-chain processes.
This reduces the need for heavy custom coding when bridging decentralized and centralized systems.

## **Hasura GraphQL Engine**
**Hasura** seamlessly manages **off-chain** data—often user details, authentication, or large volumes of records that don’t need to reside on-chain. Paired with a PostgreSQL database, Hasura automatically generates a **real-time GraphQL schema**, offering:

- **Instant Queries & Mutations**  
- **Role-Based Access Control**  
- **Real-Time Updates** for dashboards and front ends
By decoupling large or frequently changing data from blockchain storage, you optimize both performance and cost while retaining cryptographic proof references on-chain as needed.

## **S3 Storage (MinIO)**
For storing large files—such as logs, digital certificates, transaction receipts—SettleMint offers an **S3-compatible MinIO** service. You can:

- **Upload & Retrieve Files via Standard S3 APIs**  
- **Control Access Permissions**  
- **Benefit from High-Performance Object Storage**
It’s ideal for data that doesn’t require on-chain immutability or public distribution (unlike IPFS). Typical use cases include operational logs, user-generated content, and archives that must remain accessible and secure.

## **IPFS Storage**
SettleMint integrates **IPFS** for **decentralized**, **tamper-proof** file storage. A unique hash (CID) identifies each file, enabling:

- **Verified Authenticity:** Hash-based references confirm file content hasn’t changed.  
- **Permanent Distribution:** Files remain online as long as peers host them, removing dependency on a single provider.  
- **Ideal for NFTs, Public Certificates, and Audit Logs** that require trustless verification.
By offloading large files to IPFS and storing only the hash on-chain, you can preserve blockchain efficiency while retaining provable data integrity.

## **Private Key Management**
Depending on risk, compliance requirements, and scale, SettleMint supports multiple approaches:

- **Accessible ECDSA P-256:** Straightforward software-based storage.  
- **Hierarchical Deterministic (HD) ECDSA P-256:** Generate multiple child keys from a master seed for structured backups.  
- **Hardware Security Modules (HSMs):** Tamper-resistant devices ensuring maximum security for enterprise or regulated use cases.
Each approach integrates with the **Transaction Signer**, guaranteeing seamless and secure execution of on-chain operations.

## **Access Tokens (PAT/AAT)**
Two forms of token-based authentication and authorization:

- **Personal Access Tokens (PATs):** Tied to individual users for tasks like contract deployment, node setup, or platform configuration.  
- **Application Access Tokens (AATs):** For machine-to-machine interactions, often used by microservices or scripts that require secure blockchain access.
Admins can create, rotate, or revoke tokens, applying granular role-based controls to ensure only authorized entities interact with the network.

## **Custom Deployments**
SettleMint enables developers to containerize custom applications—front-end dashboards, specialized microservices, or custom oracles—and host them within the platform. You can:

- **Define Container Images & Environments**  
- **Configure Domains & SSL**  
- **Scale Resources** based on user traffic
This integrated approach eliminates the need for separate hosting services, simplifying operational overhead and unifying observability.

## **Flexible Overall Platform Deployment**
Two main models help organizations meet their security and operational needs:

1. **Managed SaaS:** SettleMint handles the underlying infrastructure, updates, and scaling on major cloud providers (AWS, Google Cloud, Azure).  
2. **Self-Managed:** Deploy the platform in your private data center or private cloud for maximum autonomy and compliance control.

## **Pricing Models**

- **SaaS (Pay-as-You-Go):** Each deployed component is charged based on usage. Shared clusters suit development phases, while dedicated clusters are recommended for production.  
- **On-Premises (Fixed Licensing):** A fixed cost per component, ideal for organizations needing strict data governance or extended custom setups. Long-term contracts exist for both models to stabilize budgeting.

## **Help and Support**
The SettleMint **Blockchain Academy**, with video tutorials, bootcamps, and “BUIDL sessions,” equips developers and enterprises with the knowledge to build robust solutions. Support is offered via:

- **Four SLA Tiers (Standard, Silver, Gold, Platinum)**  
- **Dedicated Success Teams**  
- **Channels like Discord, Slack, Email, Phone, and Video Calls**

This multi-layered support ensures timely assistance, whether you need architectural guidance or immediate debugging help.

## **Security and Compliance**
Adherence to **SOC 2 Type II**, **ISO 27001**, and **ISO 9001** standards showcases SettleMint’s commitment to data protection and operational reliability. It integrates advanced authentication protocols (OAuth, SAML, JWT) and secrets management (HashiCorp Vault), enforcing **role-based access control (RBAC)** and **encryption at rest and in transit**. For on-prem users, HTTP Basic Authentication can further safeguard API requests. These layers ensure a “defense-in-depth” security framework for industries like finance, healthcare, and government.

---

# 3. Application Development Journey on SettleMint

## A. Summary of the Development Journey

SettleMint guides you through a **practical series of stages**:

1. **Foundation Setup** (network and node configuration)  
2. **Smart Contract Development** (code, test, deploy)  
3. **Middleware & API Creation** (auto-generated REST/GraphQL endpoints)  
4. **Off-Chain Integration** (storage, databases, enterprise systems)  
5. **Security & Compliance** (private key management, token-based authentication)  
6. **Deployment & Scaling** (packaging your app for production)

## B. Detailed Steps in the Journey

Below is a deeper look at each phase, plus a **Brief Step-by-Step Guide** to help you create a working blockchain app quickly.

### 1. Lay the Foundation
Use the **Blockchain Network Manager** to configure a public (e.g., Ethereum) or private (e.g., Besu, Quorum, Fabric) network. Deploy **Blockchain Nodes**—validating for consensus, non-validating for load distribution. Add a **Blockchain Load Balancer** to handle traffic and set up the **Transaction Signer** for secure transaction submissions. Finally, confirm everything is operational in the **Blockchain Explorer**.

<ins>Brief Step-by-Step Guide:</ins>
1. Define application scope (supply chain, identity, etc.).  
2. In the Network Manager, select and configure your network (public or private).  
3. Spin up validating or non-validating nodes.  
4. Enable load balancing and secure transaction signing.  
5. Check network activity and node health in the Explorer.

### 2. Develop and Deploy Smart Contracts
Write on-chain logic in **Code Studio** (Solidity/Chaincode) or the **SDK CLI**. Rely on frameworks like Foundry/Hardhat for testing, then compile and deploy once you’re satisfied. The platform tracks deployments for easy rollback and version control.

<ins>Brief Step-by-Step Guide:</ins>
1. Write your contract using Code Studio or your preferred IDE.  
2. Test thoroughly using built-in or external test frameworks.  
3. Compile and deploy to a test network.  
4. Inspect events in the Explorer to verify success.  
5. Move to production upon final validation.

### 3. Enable APIs and Middleware
The **Smart Contract API Portal** converts your contract ABI into immediate REST or GraphQL endpoints. The **Graph Middleware** handles read operations, indexing on-chain data for fast queries. If required, the **Ethereum Attestation Indexer** can manage trust attestations for identity or compliance.

<ins>Brief Step-by-Step Guide:</ins>
1. Upload your contract ABI to the Smart Contract API Portal.  
2. Check automatically generated REST/GraphQL endpoints.  
3. Configure Graph Middleware for event indexing, if needed.  
4. Add specialized indexers (e.g., EAS) for credential or compliance data.  
5. Test endpoints in a simple front end or script.

### 4. Integrate and Finalize the Application
Enterprise-grade dApps often require off-chain data handling. Connect **S3 (MinIO)** or **IPFS** for files, and use **Hasura** on PostgreSQL for structured data. Meanwhile, orchestrate off-chain triggers with the **Integration Studio** (e.g., emailing the admin after a token transfer). By the end, your blockchain logic seamlessly interacts with centralized services.

<ins>Brief Step-by-Step Guide:</ins>
1. Decide on S3 vs. IPFS for file needs.  
2. Implement Hasura GraphQL for off-chain data queries and updates.  
3. Configure events in Integration Studio to automate workflows.  
4. Sync on-chain calls and off-chain records in real time.  
5. Confirm data consistency and reliability via logs or Explorer audits.

### 5. Secure and Comply
Select the right private key management strategy—software, HD wallets, or HSM—based on your security profile. Use **Access Tokens (PAT/AAT)** for controlling platform or API interactions. Align deployments with recognized certifications (ISO 27001, SOC 2) to ease compliance processes.

<ins>Brief Step-by-Step Guide:</ins>
1. Pick a key management approach that fits your risk tolerance.  
2. Issue PATs for developers, AATs for back-end services.  
3. Set up logging, monitoring, and regular security reviews.  
4. Conduct or schedule compliance audits as needed.  
5. Document any custom security protocols for internal reference.

### 6. Deploy, Monitor, and Scale
Finally, **containerize** your front end (React, Angular, Vue) and back-end microservices. SettleMint’s **Custom Deployments** module makes updates simpler—no downtime or big reconfigurations. Continuous monitoring checks performance and security, letting you expand capacity as your user base grows.

<ins>Brief Step-by-Step Guide:</ins>
1. Package all components into containers.  
2. Deploy them (SaaS or Self-Managed) via SettleMint’s interface.  
3. Benchmark performance under typical and peak loads.  
4. Fine-tune scaling rules and resource allocations.  
5. Iterate on your solution as usage patterns evolve.

---

# 4. Platform Deployment Options

## Managed SaaS Deployment
In **Managed SaaS**, SettleMint handles infrastructure, scaling, and patching on cloud providers like AWS, Google Cloud, or Azure. This model suits teams seeking rapid production readiness and minimal DevOps overhead, letting them concentrate on **application logic** rather than operational maintenance.

## Self-Managed Deployment
Organizations requiring total control—often due to data residency laws or internal governance—can **self-manage** the platform on-premises or in a private cloud. While more resource-intensive, this approach grants **fine-grained customization** of every layer (firewalls, compliance tools, etc.), making it attractive for heavily regulated environments.

---

# 5. Security and Compliance

Security underpins each element of SettleMint, from **network-level encryption** to **role-based access**. This layered design ensures that data, credentials, and transactions stay protected as you develop and deploy new functionalities.

## Overall Platform Security
SettleMint employs a **defense-in-depth** strategy, isolating services and requiring explicit authentication between them. Tools like **HashiCorp Vault** safeguard secrets, while real-time logs and monitoring detect anomalies. Granular access policies further limit exposure, preventing unauthorized resource access.

## Platform Certifications
By conforming to **ISO 27001, SOC 2, and ISO 9001**, SettleMint meets recognized benchmarks in data handling, operational security, and quality control. Such certifications streamline compliance for businesses in finance, healthcare, government, or other regulated industries.

## Private Key Management
The platform supports multiple key storage methods—**software wallets**, **HD wallets**, or **HSMs**—ensuring you can select the level of security that aligns with your specific requirements. This integration with the **Transaction Signer** keeps private keys protected yet readily usable for on-chain operations.

## Access Tokens
**Personal Access Tokens (PATs)** authorize individual developers, while **Application Access Tokens (AATs)** secure automated processes. Both token types can be tightly scoped, and administrators can revoke or rotate them as threats or organizational roles change.

---

# 6. Help and Support

Even with a low-code platform, blockchain can be challenging. SettleMint offers:

- **A Knowledge Base of Common Issues:** Quickly find solutions to recurring errors.  
- **Community Platforms (Discord, Slack, GitHub):** Real-time input from experts and peers.  
- **Support Tickets & SLAs:** Prioritized assistance with guaranteed response times, scaling to your SLA tier (Standard, Silver, Gold, Platinum).  
- **Blockchain Academy:** Video tutorials, bootcamps, and “BUIDL sessions” for deeper learning.

Whether you need quick fixes, specialized training, or strategic guidance, these channels ensure that you can move forward confidently at every stage of your blockchain journey.

--
