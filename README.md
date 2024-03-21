# Solid Network Bank Configuration-as-Code (CaC)

## GitHub Codespace dev container config

### Universal

devcontainer.json
```json
{
  "image": "mcr.microsoft.com/devcontainers/universal:2",

  "onCreateCommand": "git config --global user.name ${GITHUB_USER}"
}
```

### ReactJS

devcontainer.json
```json
{
  "image": "mcr.microsoft.com/devcontainers/universal:2",
  "waitFor": "onCreateCommand",
  "onCreateCommand": "git config --global user.name ${GITHUB_USER}",
  "updateContentCommand": "npm install",
  "postCreateCommand": "",
  "postAttachCommand": {
    "server": "REACT_APP_API_GATEWAY_STAGE=${localEnv:API_GATEWAY_STAGE} npm start"
  },
  "customizations": {
    "codespaces": {
      "openFiles": [
        "src/index.js"
      ]
    }
  },
  "portsAttributes": {
    "3000": {
      "label": "Application",
      "onAutoForward": "openPreview"
    }
  },
  "forwardPorts": [
    3000
  ]
}
```