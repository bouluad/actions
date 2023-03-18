To use this composite action in a workflow, you would pass in the required inputs, like this:

```
jobs:
  example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy All to Kubernetes
        uses: your-username/deploy-all-to-kubernetes@main
        with:
          kube-config-data: ${{ secrets.KUBE_CONFIG_DATA }}
          manifest-folder: 'path/to/manifests'
          namespace: 'example-namespace'
```
Note that in the Deploy All to Kubernetes step, we're using a for loop to iterate over all .yml files in the specified folder and apply them to the Kubernetes cluster. Make sure that the manifest files in the folder are valid Kubernetes YAML files.
