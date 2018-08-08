# Deployment

> Note: Docker Compose instructions coming soon

If you want to self-host Cortex CMS, this guide is for you. Currently, only [Manual Setup](setup/manual-setup.md) is officially supported.

## Configuration

Deploying the `development` environment as a non-local server will require an additional environmental variable be set:

```text
DEPLOYED=true
```

This will configure various things such as [dotenv](https://github.com/bkeepers/dotenv) to behave normally in a deployed scenario.

