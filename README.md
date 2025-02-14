# goose-with-mcp-servers
Codename goose docker image with mcp servers


## Configuring Goose

Run `goose configure` to setup connection from goose to LLM.


Example output for Ollama (use host.docker.internal instead of localhost due to docker networking))

```
Welcome to goose! Let's get you set up with a provider.
  you can rerun this command later to update your configuration

┌   goose-configure 
│
◇  Which model provider should we use?
│  Ollama 
│
◇  Provider Ollama requires OLLAMA_HOST, please enter a value
│  host.docker.internal
│
◇  Enter a model from that provider:
│  qwen2.5
│
◓  Checking your configuration...                                                                                                                                                                                                   └  Configuration saved successfully

  Tip: Run 'goose configure' again to adjust your config or add extensions

```

## Automatic install of Goose
Devcontainer contains installing of Goose via `postCreateCommand`.
```
curl -fsSL https://github.com/block/goose/releases/download/stable/download_cli.sh | CONFIGURE=false bash
```

### Dependency
Goose requires libdbus which is also added to Devcontainer
```
sudo apt-get update && sudo apt-get install -y libdbus-1-3
```


### Add GitHub MCP Server to Goose
GitHub Personal access token added via https://github.com/settings/personal-access-tokens/

```
node ➜ /workspaces/goose-with-mcp-servers (main) $ goose configure

This will update your existing config file
  if you prefer, you can edit it directly at /home/node/.config/goose/config.yaml

┌   goose-configure 
│
◇  What would you like to configure?
│  Add Extension 
│
◇  What type of extension would you like to add?
│  Command-line Extension 
│
◇  What would you like to call this extension?
│  GitHub
│
◇  What command should be run?
│  npx -y @modelcontextprotocol/server-github
│
◇  Would you like to add environment variables?
│  Yes 
│
◇  Environment variable name:
│  GITHUB_PERSONAL_ACCESS_TOKEN
│
◇  Environment variable value:
│  ▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪▪
│
◇  Add another environment variable?
│  No 
│
└  Added GitHub extension
```