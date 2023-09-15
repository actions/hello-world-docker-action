name: Hello, World!
description: Greet someone and record the time
author: GitHub Actions

# Define your inputs here.
inputs:
  who-to-greet:
    description: Who to greet
    required: true
    default: World

# Define your outputs here.
outputs:
  time:
    description: The time we greeted you

runs:
  using: docker
  image: Dockerfile
  env:
    INPUT_WHO_TO_GREET: ${{ inputs.who-to-greet }}
