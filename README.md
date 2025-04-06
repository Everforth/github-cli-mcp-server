# Everforth GitHub MCP Server

- この MCP server は github に graphql アクセスを投げるシンプルなもの
- Motivation
  - アクセストークンをセキュアに扱う（Cursor Agent に与えない）
  - 実は[公式 MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/github)がまともに使えなかった & ProjectV2（カンバン）を使うならいずれにせよ graphql が必要
- setup 時に一度 docker build してしまえば、それ以降は cursor 経由で docker の面倒を見てくれる

## How to use

- Cursor の mcp.json に下記の `github-cli` セクションを追加してください
- `env` の `<PERSONAL_ACCESS_TOKEN>` に自分の GitHub アクセストークンを貼ってください
- Cursor を restart してください

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
        "ikutani41/github-cli-mcp-server"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<PERSONAL ACCESS TOKEN HERE>"
      }
    }
  }
}
```

## 自分でビルドして使いたい場合

- `npm install`
- `docker build -t {hoge}/github-cli-mcp-server -f Dockerfile .`

