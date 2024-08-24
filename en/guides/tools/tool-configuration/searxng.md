# SearXNG
SearXNG is a free internet metasearch engine which aggregates results from various search services and databases. Users are neither tracked nor profiled. Now you can use this tool directly in Mlchain.

Below are the steps for integrating SearXNG into Mlchain using Docker in the [Community Edition](https://docs.mlchain.khulnasoft.com/getting-started/install-self-hosted/docker-compose).

> If you want to use SearXNG within the Mlchain cloud service, please refer to the [SearXNG installation documentation](https://docs.searxng.org/admin/installation.html) to set up your own service, then return to Mlchain and fill in the service's Base URL in the "Tools > SearXNG > Authenticate" page.

## 1. Modify Mlchain Configuration File

The configuration file is located at `mlchain/api/core/tools/provider/builtin/searxng/docker/settings.yml`, and you can refer to the config documentation [here](https://docs.searxng.org/admin/settings/index.html).

## 2. Start the Service

Start the Docker container in the mlchain root directory.

```bash
cd mlchain
docker run --rm -d -p 8081:8080 -v "${PWD}/api/core/tools/provider/builtin/searxng/docker:/etc/searxng" searxng/searxng
```

## 3. Use SearXNG

Fill in the access address in "Tools > SearXNG > Authenticate" to establish a connection between the Mlchain service and the SearXNG service. The Docker internal address for SearXNG is usually `http://host.docker.internal:8081`.
