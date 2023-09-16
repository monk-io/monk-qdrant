# Qdrant meets Monk

This repository contains Monk.io template to deploy Qdrant system either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

- [Qdrant meets Monk](#qdrant-meets-monk)
  - [Prerequisites](#prerequisites)
    - [Make sure monkd is running](#make-sure-monkd-is-running)
    - [Clone Repository](#clone-repository)
    - [Load Template](#load-template)
    - [Verify if it's loaded correctly](#verify-if-its-loaded-correctly)
  - [Deploy Qdrant](#deploy-qdrant)
  - [Stop, remove and clean up workloads and templates](#stop-remove-and-clean-up-workloads-and-templates)

## Prerequisites

- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

### Make sure monkd is running

```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

### Clone Repository

```bash
git clone git@github.com:monk-io/monk-qdrant.git
```

### Load Template

```bash
cd monk-qdrant
monk load MANIFEST
```

### Verify if it's loaded correctly

```bash
$ monk list -l qdrant
✔ Got the list
Repository  Template       Version  Type      Tags
local       qdrant/base    1.0      runnable  search, search-engine, machine-learning, neural-network, matching, nearest-neighbor-search...
local       qdrant/server  1.0      runnable  search, search-engine, machine-learning, neural-network, matching, nearest-neighbor-search...
```

## Deploy Qdrant

```bash
$ monk run qdrant/server
✔ Starting the run job: local/qdrant/server... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% qdrant/qdrant:latest local
✔ Checking/pulling images DONE
✔ Starting containers DONE
✔ New container local-86720f0e00acc4c3a71f018d90-local-qdrant-server-qdrant created DONE
✔ Started local/qdrant/server
🔩 templates/local/qdrant/server
 └─🧊 Peer local
    └─🔩 templates/local/qdrant/server
       └─📦 local-86720f0e00acc4c3a71f018d90-local-qdrant-server-qdrant running
          ├─🧩 qdrant/qdrant:latest
          ├─💾 /var/lib/monkd/volumes/qdrant/storage -> /qdrant/storage
          └─🔌 open 1.1.1.1:6333 -> 6333

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/qdrant/server - Inspect logs
        monk shell     local/qdrant/server - Connect to the container's shell
        monk do        local/qdrant/server/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Stop, remove and clean up workloads and templates

```bash
monk purge    qdrant/server
monk purge -x qdrant/server
```
