# Post JSON to URL Action

This action allows you to send JSON data to a specified URL using curl.

## Inputs

- `URL`: The URL where the JSON will be sent (required)
- `AUTHORIZATION`: The authorization header content for the API (required)
- `JSON`: The JSON data that will be sent to the URL (required)

## Outputs

- `response`: The response received from the API

## Example usage

```yaml
on: push

jobs:
  post_json:
    runs-on: ubuntu-latest

    steps:
      - name: Post JSON to URL
        uses: anyscripts/post-json@v1.0.0
        with:
          URL: 'https://api.example.com/endpoint'
          AUTHORIZATION: Bearer ${{ secrets.API_TOKEN }}
          JSON: '{"data": "example"}'
      - name: Echo response
        run: echo ${{ steps.post_json.outputs.response }}

```

In this example, the action is triggered on a `push` event, and the `post_json` job is run. The action is called in the
first step, and the `URL`, `TOKEN`, and `JSON` inputs are passed to it. In this example, the `TOKEN` input is passed as
a secret, which is a secure way to store sensitive information.

The second step runs the command `echo ${{ steps.post_json.outputs.response }}` to display the response received from the
API in the job logs.