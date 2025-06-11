## Github_JWT_Demo
Conjur YAML documents and actions workflow scripts for demonstrating Conjur JWT integration with Github


# OIDC Authentication Details

This action uses GitHub's OpenID Connect (OIDC) token to authenticate to Conjur. When configured correctly, GitHub generates a short-lived OIDC token for your workflow that Conjur can validate using GitHub's JWKS endpoint.

The claims in the OIDC token include:

jwks: The github public jwks (always "https://token.actions.githubusercontent.com/.well-known/jwks")  
sub: A unique identifier for the workflow run  
aud: The audience (always "https://github.com/YOUR-ORG/YOUR-REPO")  
iss: The issuer (always "https://token.actions.githubusercontent.com")  
repository: The repository name (e.g., "your-org/your-repo")  
Additional claims related to the workflow, job, and runner  

The workflow claim is a good candidate for token-app-property, as it does not include any characters that need to be url encoded