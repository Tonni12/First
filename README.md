# First
graph LR
    %% Styling
    classDef inception fill:#f9f0ff,stroke:#d0a9f5,stroke-width:2px;
    classDef dev fill:#e6f7ff,stroke:#91d5ff,stroke-width:2px;
    classDef cicd fill:#fffbe6,stroke:#ffe58f,stroke-width:2px;
    classDef prod fill:#f6ffed,stroke:#b7eb8f,stroke-width:2px;

    %% Inception Phase
    subgraph Phase 1: Inception & Design
        Idea((💡 Inception)) --> Req[📝 Requirements & Compliance]
        Req --> SysDesign[🏗️ System Architecture]
    end
    class Idea,Req,SysDesign inception;

    %% Development Phase
    subgraph Phase 2: Development
        SysDesign --> Code[💻 Code Generation]
        Code --> PR[🔀 Git Pull Request]
    end
    class Code,PR dev;

    %% CI/CD Pipeline
    subgraph Phase 3: Automated CI/CD Pipeline
        PR --> Build[🐳 Build Docker Images]
        Build --> Test[🧪 Automated Security & Unit Tests]
        Test --> Registry[📦 Push to Container Registry]
        Registry --> Stage[🟡 Deploy to Staging]
        Stage --> Approval{✔️ Manual QA/Approval}
    end
    class Build,Test,Registry,Stage,Approval cicd;

    %% Production Phase
    subgraph Phase 4: Production
        Approval --> ProdDeploy[🚀 Deploy to Production Kubernetes]
        ProdDeploy --> Live((🟢 Live System))
    end
    class ProdDeploy,Live prod;
