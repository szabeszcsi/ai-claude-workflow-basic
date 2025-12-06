# Dev Container Customization Guide

This guide explains how to customize `devcontainer.json` for different project types.

---

## Quick Reference

| Project Type | Key Changes |
|--------------|-------------|
| Python only | Remove Node feature (but keep for Claude CLI) |
| Node.js only | Remove Python feature |
| .NET | Add dotnet feature |
| Full-stack | Add multiple language features |
| Data Science | Add Python + Jupyter feature |
| DevOps | Add Docker-in-Docker, Azure CLI |

---

## Understanding the Structure

```jsonc
{
  "name": "...",           // Display name in VS Code
  "image": "...",          // Base Docker image
  "features": { },         // Add-on capabilities
  "customizations": { },   // VS Code settings & extensions
  "postCreateCommand": "", // Run once after container created
  "postStartCommand": "",  // Run every time container starts
  "remoteUser": "vscode"   // User to run as
}
```

---

## Common Customizations

### 1. Change Project Name

```jsonc
"name": "MyProject - AI Sandbox",
```

This shows in VS Code's status bar and container list.

---

### 2. Adjust Python Version

```jsonc
"features": {
  "ghcr.io/devcontainers/features/python:1": {
    "version": "3.11"  // or "3.10", "3.12", "3.13"
  }
}
```

---

### 3. Adjust Node.js Version

```jsonc
"features": {
  "ghcr.io/devcontainers/features/node:1": {
    "version": "20"  // or "18", "lts", "latest"
  }
}
```

> **Note:** Node.js is required for Claude Code CLI. Don't remove it unless you have another way to run Claude.

---

### 4. Add .NET

```jsonc
"features": {
  // ... existing features ...
  "ghcr.io/devcontainers/features/dotnet:1": {
    "version": "8.0"  // or "7.0", "6.0"
  }
}
```

And add extension:
```jsonc
"extensions": [
  // ... existing ...
  "ms-dotnettools.csharp",
  "ms-dotnettools.csdevkit"
]
```

---

### 5. Add Go

```jsonc
"features": {
  "ghcr.io/devcontainers/features/go:1": {
    "version": "latest"
  }
}
```

---

### 6. Add Rust

```jsonc
"features": {
  "ghcr.io/devcontainers/features/rust:1": {
    "version": "latest"
  }
}
```

---

### 7. Add Docker-in-Docker

For projects that need to build/run Docker containers:

```jsonc
"features": {
  "ghcr.io/devcontainers/features/docker-in-docker:1": {}
}
```

---

### 8. Add Azure CLI

```jsonc
"features": {
  "ghcr.io/devcontainers/features/azure-cli:1": {}
}
```

---

### 9. Add PowerShell

```jsonc
"features": {
  "ghcr.io/devcontainers/features/powershell:1": {}
}
```

---

### 10. Customize Post-Create Command

The `postCreateCommand` runs once when the container is first created.

**Python project with requirements:**
```jsonc
"postCreateCommand": "pip install -r requirements.txt && npm install -g @anthropic-ai/claude-code"
```

**Node.js project:**
```jsonc
"postCreateCommand": "npm install && npm install -g @anthropic-ai/claude-code"
```

**Python + Node.js:**
```jsonc
"postCreateCommand": "pip install -r requirements.txt && npm install && npm install -g @anthropic-ai/claude-code"
```

**With dev dependencies:**
```jsonc
"postCreateCommand": "pip install -r requirements.txt -r requirements-dev.txt && npm install -g @anthropic-ai/claude-code"
```

---

### 11. Add Port Forwarding

For web development, forward ports to your host:

```jsonc
"forwardPorts": [3000, 5000, 8000, 8080],
```

---

### 12. Add Environment Variables

```jsonc
"containerEnv": {
  "PYTHONDONTWRITEBYTECODE": "1",
  "NODE_ENV": "development",
  "MY_API_KEY": "${localEnv:MY_API_KEY}"  // Pass from host
}
```

---

### 13. Add VS Code Extensions

Find extension IDs from VS Code marketplace or by right-clicking installed extensions.

```jsonc
"extensions": [
  // Python
  "ms-python.python",
  "ms-python.vscode-pylance",
  "ms-python.black-formatter",
  
  // JavaScript/TypeScript
  "dbaeumer.vscode-eslint",
  "esbenp.prettier-vscode",
  
  // Data/SQL
  "ms-mssql.mssql",
  "mechatroner.rainbow-csv",
  
  // Docker
  "ms-azuretools.vscode-docker",
  
  // Git
  "eamodio.gitlens",
  "mhutchie.git-graph",
  
  // Markdown
  "yzhang.markdown-all-in-one",
  "davidanson.vscode-markdownlint"
]
```

---

## Example Configurations

### Python Data Science Project

```jsonc
{
  "name": "Data Science - AI Sandbox",
  "image": "mcr.microsoft.com/devcontainers/base:ubuntu",
  "features": {
    "ghcr.io/devcontainers/features/python:1": {
      "version": "3.11"
    },
    "ghcr.io/devcontainers/features/node:1": {
      "version": "lts"
    }
  },
  "customizations": {
    "vscode": {
      "extensions": [
        "ms-python.python",
        "ms-python.vscode-pylance",
        "ms-toolsai.jupyter",
        "mechatroner.rainbow-csv"
      ]
    }
  },
  "postCreateCommand": "pip install pandas numpy scikit-learn jupyter matplotlib && npm install -g @anthropic-ai/claude-code",
  "remoteUser": "vscode"
}
```

### Full-Stack Web Project

```jsonc
{
  "name": "Full-Stack - AI Sandbox",
  "image": "mcr.microsoft.com/devcontainers/base:ubuntu",
  "features": {
    "ghcr.io/devcontainers/features/python:1": { "version": "3.12" },
    "ghcr.io/devcontainers/features/node:1": { "version": "20" },
    "ghcr.io/devcontainers/features/docker-in-docker:1": {}
  },
  "customizations": {
    "vscode": {
      "extensions": [
        "ms-python.python",
        "dbaeumer.vscode-eslint",
        "esbenp.prettier-vscode",
        "ms-azuretools.vscode-docker"
      ]
    }
  },
  "forwardPorts": [3000, 8000],
  "postCreateCommand": "pip install -r requirements.txt && npm install && npm install -g @anthropic-ai/claude-code",
  "remoteUser": "vscode"
}
```

### Minimal (Claude Code Only)

```jsonc
{
  "name": "Minimal - AI Sandbox",
  "image": "mcr.microsoft.com/devcontainers/base:ubuntu",
  "features": {
    "ghcr.io/devcontainers/features/node:1": { "version": "lts" }
  },
  "postCreateCommand": "npm install -g @anthropic-ai/claude-code",
  "remoteUser": "vscode"
}
```

---

## Finding More Features

Browse available features:
- Official: https://containers.dev/features
- GitHub: https://github.com/devcontainers/features

---

## Troubleshooting

### Container won't build
- Check JSON syntax (use VS Code's JSON validation)
- Remove comments (`//`) if your Docker version doesn't support jsonc
- Check feature names are spelled correctly

### Feature not found
- Check the feature URL is correct
- Some features may have been renamed or deprecated
- Try `ghcr.io/devcontainers/features/` prefix

### Out of disk space
- Clean up Docker: `docker system prune -a`
- Use smaller base image
- Remove unused features

### Slow container start
- Reduce number of features
- Use pre-built image instead of building from features
- Consider creating a custom Dockerfile

---

## Converting to Dockerfile (Advanced)

If you need more control, you can use a Dockerfile instead:

```jsonc
{
  "name": "Custom - AI Sandbox",
  "build": {
    "dockerfile": "Dockerfile",
    "context": ".."
  },
  // ... rest of config
}
```

Then create `.devcontainer/Dockerfile` with your custom setup.
