# Everforth GitHub MCP Server

## usage

- clone
- cd to the cloned directory
- `npm install`
- `docker build -t mcp/github-cli-mcp-server -f Dockerfile .`

## Cursor MCP config

```
{
  "mcpServers": {
    "github-graphql-cli": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "GITHUB_PERSONAL_ACCESS_TOKEN",
        "mcp/github-cli-mcp-server"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<PERSONAL ACCESS TOKEN HERE>"
      }
    }
  }
}
```
