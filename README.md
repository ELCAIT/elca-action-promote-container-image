# GitHub Action to Promote Container Image

## Usage
```yaml
# On GitHub.com
name: 'Promote Container Image'
on:
  workflow_dispatch:
    inputs:
      current-image-tag:
        description: "Exising container image tag to promote (i.e.: e795e234b23f86f895e7b4aeb292d56406f54e9d)"
        required: true
        type: string
      new-image-tag:
        description: "New container image tag (i.e.: 2.0.0)"
        required: true
        type: string

jobs:
  promote-container-image:
    name: 'Promote Container Image'
    timeout-minutes: 5
    runs-on: ubuntu-latest
    steps:
      - uses: ELCAIT/elca-action-promote-container-image@1.0.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          image-name: ELCAIT-my-org/my-repo/my-docker-image-name
          current-image-tag: ${{ inputs.current-image-tag }}
          new-image-tag: ${{ inputs.new-image-tag }}

# On-premise GitHub server
name: 'Promote Container Image'
on:
  workflow_dispatch:
    inputs:
      current-image-tag:
        description: "Exising container image tag to promote (i.e.: e795e234b23f86f895e7b4aeb292d56406f54e9d)"
        required: true
        type: string
      new-image-tag:
        description: "New container image tag (i.e.: 2.0.0)"
        required: true
        type: string

jobs:
  promote-container-image:
    name: 'Promote Container Image'
    timeout-minutes: 5
    runs-on: ubuntu-latest
    steps:
      - uses: ELCAIT/elca-action-promote-container-image@1.0.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          container-registry: docker.xxx.com
          image-name: ELCAIT-my-org/my-repo/my-docker-image-name
          current-image-tag: ${{ inputs.current-image-tag }}
          new-image-tag: ${{ inputs.new-image-tag }}
```
