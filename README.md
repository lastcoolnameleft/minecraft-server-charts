# Minecraft Server Chats

This repo is designed as a template for a Microsoft Partner to create a Kubernetes App in the Azure Marketplace.

## Testing

Prior to pushing the offer to the Azure Marketplace, make sure to validate the helm install

```
helm install ./charts/minecraft --generate-name --dry-run --debug
```

# GitHub Actions

The [GitHub Action Workflow](.github/workflows/CNABPackage.yml) will bundle the package and then publish to the ACR described in the manifest file.  The Action Workflow will work out of the box with a few changes to the repository settings:

1. A Repository Secret Named "AZURE_ACR" will need to be created with the name of the ACR in your manifest file.  This is used in the "Build and Publish Bundle" step.
    1. On the top of the repository select "Settings"
    2. On the left hand side select "Secrets" followed by "Actions" in the dropdown.
    3. Select "New repository secret"
    4. In the name, enter "AZURE_ACR"
    5. For the secret, enter your ACR login server.
2. For the "OIDC Login to Azure Public Cloud" step, we need to provide the AZURE_CLIENT_ID, AZURE_SUBSCRIPTION_ID, and AZURE_TENANT_ID of your service principal which has access to the ACR.  You can add the respective secrets using the same steps as the AZURE_ACR secret.
    * For additional information about OIDC Setup with GitHub and Azure, please reference the link [here](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-azure)

## Notes

Inspired by https://github.com/itzg/minecraft-server-charts