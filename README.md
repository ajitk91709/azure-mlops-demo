What Each Folder Is For

src/ — Your actual ML code

    data/ → data loaders, feature readers
    
    models/ → model classes, wrappers
    
    pipelines/ → training/inference pipelines
    
    training/ → training entrypoints
    
    inference/ → batch/online scoring code
    
    utils/ → shared helpers

This keeps your ML code clean and modular.

infrastructure/ — Azure IaC

Supports Bicep, Terraform, or ARM:

    Provision Azure ML Workspace
    
    Create compute clusters
    
    Create storage accounts
    
    Create Key Vault
    
    Create Container Registry
    
    Create Managed Online Endpoints

This ensures reproducible cloud environments.

.github/workflows/ or azure-pipelines.yml — CI/CD
Typical pipelines:

  train.yml → triggers training pipeline
  
  register.yml → registers model in Azure ML registry
  
  deploy.yml → deploys to staging/prod endpoints

Use GitHub Actions or Azure DevOps depending on your org.

environments/ — Reproducible environments
Include:

    requirements.txt → pip environment
    
    environment.yml → conda environment
    
    conda-mlflow.yml → MLflow training environment

Azure ML uses these to build deterministic Docker images.

configs/ — Environment‑specific settings
Examples:

    dev.env, prod.env → environment variables
    
    aml_config.json → Azure ML workspace config

Your Python code loads these via dotenv.

notebooks/ — Exploration & Databricks notebooks
Keep notebooks separate from production code.

tests/ — Unit, integration, E2E
Supports CI/CD quality gates.

scripts/ — Automation scripts
Examples:

    run_training.py → CLI training entrypoint
    
    register_model.py → MLflow/Azure ML registration
    
    run_batch_scoring.py → batch inference
