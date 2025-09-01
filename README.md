# babbelfisch-n8n-agents 🤖

Official documentation:
https://docs.n8n.io/

## Getting Started
* Copy and fill the `template.env`. Rename it to `local.env` to provide environment variables (see: `<TODO>`)
* Run n8n-docker-compose.yml to start up the n8n self-hosted service:
     ```shell
     podman-compose -f docker-compose.yml up -d
     # if you have a docker license:
     docker compose -f docker/docker-compose.yml up -d
     ```
* Open http://localhost:5678/ and create a fake owner account
* Create a credential for iteraGPT API https://docs.n8n.io/credentials/add-edit-credentials/ with a unique API Key.
* Start building agents 🤖
