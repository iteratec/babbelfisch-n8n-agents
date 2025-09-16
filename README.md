# babbelfisch-n8n-agents 🤖

Official documentation:
https://docs.n8n.io/

## Getting Started
* Copy and fill the `template.env`. Rename it to `local.env` to provide environment variables (see: `<TODO>`).
Passwords for n8n can be generated securely via
  ```bash
  openssl rand -base64 32
  ```

* Run n8n-docker-compose.yml to start up the n8n self-hosted service:
     ```shell
     podman-compose -f docker-compose.yml up -d
     # if you have a docker license:
     docker compose -f docker/docker-compose.yml up -d
     ```
* Open http://localhost:5678/ and create a fake owner account
* Create a credential for iteraGPT API https://docs.n8n.io/credentials/add-edit-credentials/ with a unique API Key.
* Start building agents 🤖

## Setup Workflows

-  Redis

    Redis is included in the Docker Compose setup. Snapshots are saved automatically (REDIS_ARGS=--save 60 1000):
    - every 60 seconds,
    - but only if at least 1000 keys have changed in that time

* Qdrant
    - Currently runs without API key

* Workflows

    To use the provided JSON workflows you need to import them manually and re-connect subworkflows:

    1. **Create a new workflow** in n8n.
    2. **Rename the workflow** so its name matches the JSON file you want to import  
   (e.g. if the file is `projekt_referenz_schreiber.json`, rename the workflow to `projekt_referenz_schreiber`).
    3. **Import the JSON file** into the newly created workflow.
    4. After all JSONs are uploaded, you must **reapply the subworkflows** for `projekt_referenz_interview`:
   - Open the node that calls a subworkflow.
   - Select the workflow that matches the node’s name.  
     For example, in `projekt_referenz_interview` there is a node calling `projekt_referenz_schreiber`.  
     You need to open that node and select the workflow `projekt_referenz_schreiber` manually,  
     since this is not done automatically by n8n.

    ➡️ In the future this process could be automated via the CLI (`n8n import:workflow`), but for now the manual steps above are required.  
    - Alternative: CLI import (see [n8n import docs](https://docs.n8n.io/hosting/cli-commands/#import-workflows-and-credentials)).

* Community Nodes
  - The Community Node "n8n-nodes-qdrant" may be required
  - See [Community Nodes in n8n](https://docs.n8n.io/integrations/community-nodes/installation/) for installation instructions