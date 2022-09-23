# Minecraft Server Chats

This repo is designed as a template for a Microsoft Partner to create a Kubernetes App in the Azure Marketplace.

## Usage

For details, see: https://github.com/Azure/containersmarketplace_ext/blob/main/packaging-container-app.md

## Testing

```
helm install ./charts/minecraft --generate-name --dry-run --debug
```

## Notes

Inspired by https://github.com/itzg/minecraft-server-charts