# Hello world docker action

This action prints "Hello World" to the log or "Hello" + the name of a person to greet. To learn how this action was built, see "[Creating a Docker container action](https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action)" in the GitHub Docs.

## Inputs

### `who-to-greet`

**Required** The name of the person to greet. Default `"World"`.

## Outputs

### `time`

The time we greeted you.

## Example usage

```yaml
uses: actions/hello-world-docker-action@main
with:
  who-to-greet: 'Mona the Octocat
```
Updated
