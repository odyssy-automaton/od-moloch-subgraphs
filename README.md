# od-moloch-subgraph

Repo for quick deployments of moloch clone subgraphs to The Graph.

## Deployment

Each subgraph is in a branch in this repo. Moloch contract and Graph specific details are changed per branch.

1. Create a new subgraph on you TheGraph dashboard.

2. Clone and yarn install this repo.

3. Checkout a new branch with the name of the moloch

```bash
git checkout -b moloch/double-dog-dare-dao
```

5. Modify subgraph.yaml with new moloch contract address on line 11.

```yaml
source:
  address: "0x123...."
  abi: Moloch
```

6. Modidy the package.json scripts to point at the new graph created in step 1.

```json
  "scripts": {
    "codegen": "graph codegen",
    "build": "graph build",
    "deploy": "graph deploy --node https://api.thegraph.com/deploy/ --ipfs https://api.thegraph.com/ipfs/ <org-name>/<graph-name>",
    "create-local": "graph create --node http://localhost:8020/ <org-name>/<graph-name>",
    "remove-local": "graph remove --node http://localhost:8020/ <org-name>/<graph-name>",
    "deploy-local": "graph deploy --node http://localhost:8020/ --ipfs http://localhost:5001 <org-name>/<graph-name>"
  },
```

7. Once you're authenticated into the subgraph dashboard you can deploy with the graph cli:

```bash
yarn codegen && yarn build && yarn deploy
```
