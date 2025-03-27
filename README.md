# Everforth GitHub MCP Server

- このMCP serverはgithubにgraphqlアクセスを投げるシンプルなもの
- Motivationは2つ
  - カンバン（ProjectV2）を使ったり、柔軟性の高いクエリを実行するなら[Restful APIベースの公式MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/github)よりGraphQLベースのアクセスの方が便利
  - Cursor Agentのターミナルからcurl実行させようとするとPersonal Access Tokenをセキュアに扱うのが難しそうだったため構築した
- 公式MCPはresponseがでかすぎてまともに使えない（responseもプロトコル準拠してなくてエラーになる）ので、まだ実用できるものではなさそうだった

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
