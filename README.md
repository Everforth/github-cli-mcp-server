# Everforth GitHub MCP Server

- この MCP server は github に graphql アクセスを投げるシンプルなもの
- Motivation
  - アクセストークンをセキュアに扱う（Cursor Agent に与えない）
  - 実は[公式 MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/github)がまともに使えなかった & ProjectV2（カンバン）を使うならいずれにせよ graphql が必要
- setup 時に一度 docker build してしまえば、それ以降は cursor 経由で docker の面倒を見てくれる

## setup

- clone
- cd to the cloned directory
- `npm install`
- `docker build -t mcp/github-cli-mcp-server -f Dockerfile .`
- add cursor configuration in mcp.json
  - make sure to replace your `PERSONAL ACCESS TOKEN` in env.
- restart cursor

```
{
  "mcpServers": {
    "github-cli": {
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
