# Hello, World! Docker Action

[![GitHub Super-Linter](https://github.com/actions/hello-world-docker-action/actions/workflows/linter.yml/badge.svg)](https://github.com/super-linter/super-linter)
![CI](https://github.com/actions/hello-world-docker-action/actions/workflows/ci.yml/badge.svg)

This action prints `Hello, World!` or `Hello, <who-to-greet>!` to the log. To
learn how this action was built, see
[Creating a Docker container action](https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action).

## Create Your Own Action

To create your own action, you can use this repository as a template! Just
follow the below instructions:

1. Click the **Use this template** button at the top of the repository
1. Select **Create a new repository**
1. Select an owner and name for your new repository
1. Click **Create repository**
1. Clone your new repository

> [!CAUTION]
>
> Make sure to remove or update the [`CODEOWNERS`](./CODEOWNERS) file! For
> details on how to use this file, see
> [About code owners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners).

## Usage

Here's an example of how to use this action in a workflow file:

```yaml
name: Example Workflow

on:
  workflow_dispatch:
    inputs:
      who-to-greet:
        description: Who to greet in the log
        required: true
        default: 'World'
        type: string

jobs:
  say-hello:
    name: Say Hello
    runs-on: ubuntu-latest

    steps:
      # Change @main to a specific commit SHA or version tag, e.g.:
      # actions/hello-world-docker-action@e76147da8e5c81eaf017dede5645551d4b94427b
      # actions/hello-world-docker-action@v1.2.3
      - name: Print to Log
        id: print-to-log
        uses: actions/hello-world-docker-action@main
        with:
          who-to-greet: ${{ inputs.who-to-greet }}
```

For example workflow runs, check out the
[Actions tab](https://github.com/actions/hello-world-docker-action/actions)!
:rocket:

## Inputs

| Input          | Default | Description                     |
| -------------- | ------- | ------------------------------- |
| `who-to-greet` | `World` | The name of the person to greet |

## Outputs

| Output | Description             |
| ------ | ----------------------- |
| `time` | The time we greeted you |

## Test Locally

After you've cloned the repository to your local machine or codespace, you'll
need to perform some initial setup steps before you can test your action.

> [!NOTE]
>
> You'll need to have a reasonably modern version of
> [Docker](https://www.docker.com/get-started/) handy (e.g. docker engine
> version 20 or later).

1. :hammer_and_wrench: Build the container

   Make sure to replace `actions/hello-world-docker-action` with an appropriate
   label for your container.

   ```bash
   docker build -t actions/hello-world-docker-action .
   ```

1. :white_check_mark: Test the container

   You can pass individual environment variables using the `--env` or `-e` flag.

   ```bash
   $ docker run --env INPUT_WHO_TO_GREET="Mona Lisa Octocat" actions/hello-world-docker-action
   ::notice file=entrypoint.sh,line=7::Hello, Mona Lisa Octocat!
   ```

   Or you can pass a file with environment variables using `--env-file`.

   ```bash
   $ echo "INPUT_WHO_TO_GREET=\"Mona Lisa Octocat\"" > ./.env.test

   $ docker run --env-file ./.env.test actions/hello-world-docker-action
   ::notice file=entrypoint.sh,line=7::Hello, Mona Lisa Octocat!
   ```
