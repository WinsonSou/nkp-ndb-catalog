# NKP Custom Catalog Application: NDB PostgreSQL

To add this to a project simply create a gitrepository resource as shown below to the given project

```
#export a NAMESPACE variable pointing to the workspace on the management cluster.
#to find the workspace namespace, use the `nkp get workspaces` command
export WORKSPACE_NAMESPACE=lazarus-workspace
```

```
kubectl apply -f - <<EOF
apiVersion: source.toolkit.fluxcd.io/v1
kind: GitRepository
metadata:
  name: ndb-postgres
  namespace: ${WORKSPACE_NAMESPACE}
  labels:
    kommander.d2iq.io/gitapps-gitrepository-type: catalog
    kommander.d2iq.io/gitrepository-type: catalog
spec:
  interval: 1m0s
  ref:
    branch: main
  timeout: 20s
  url: https://github.com/WinsonSou/nkp-ndb-catalog.git
EOF

``` 


Install the App from the App catalog
