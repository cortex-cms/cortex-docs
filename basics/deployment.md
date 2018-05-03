# Deployment

> Note: Docker Compose instructions coming soon

If you want to self-host Cortex CMS, this guide is for you. Currently, only [Manual Setup](setup/manual.md) is officially supported.

## Configuration

To use an automated tool to deploy the server, set this environmental variable:

```text
CI=true
```

This will suppress Bower's interactive request to enable insights/metrics reporting, which normally prevents the CI process from continuing.

Additionally, deploying the `development` environment as a non-local server will require an additional environmental variable be set:

```text
DEPLOYED=true
```

This will configure various things such as [dotenv](https://github.com/bkeepers/dotenv) to behave normally in a deployed scenario.

