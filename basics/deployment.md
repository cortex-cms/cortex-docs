> Note: Docker Compose instructions coming soon

To use an automated tool to deploy the server, set this environmental variable:

```shell
CI=true
```

This will suppress Bower's interactive request to enable insights/metrics reporting, which normally prevents the CI process from continuing.

Additionally, deploying the `development` environment as a non-local server will require an additional environmental variable be set:

```shell
DEPLOYED=true
```

This will configure various things, such as [dotenv](https://github.com/bkeepers/dotenv) to behave normally in a deployed scenario.
