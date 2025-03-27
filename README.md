# Everforth GitHub MCP Server

- GitHubの基本的な情報取得は[公式MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/github)を使う方が設定は楽そう
- カンバン（ProjectV2）を使ったり、柔軟性の高いクエリを実行するならGraphQLベースのアクセスの方が便利
- このMCP serverはgithubにgraphqlアクセスを投げるシンプルなもの
  - Cursor Agentのターミナルからcurl実行させようとするとPersonal Access Tokenをセキュアに扱うのが難しそうだったため構築した

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
