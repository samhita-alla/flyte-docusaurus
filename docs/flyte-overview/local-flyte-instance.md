---
title: A Local Flyte Instance
---

Flyte enables scalable, reproducible and reliable orchestration of massively large workflows. To get a sense of the product, a minimalist version of the Flyte system is packaged into a Docker image.

With [docker](https://docs.docker.com/get-docker/) installed, run this command:

```
docker run --rm --privileged -p 30081:30081 -p 30082:30082 -p 30084:30084 ghcr.io/flyteorg/flyte-sandbox
```

This creates a local Flyte sandbox. Once the sandbox is ready, you should see the following message:

Flyte is ready! Flyte UI is available at `http://localhost:30081/console`.

Go ahead and visit `http://localhost:30081/console` to check it out.

Below is a quick visual tour for launching your first Workflow:

![Docusaurus](/img/first-run-console-2.gif)