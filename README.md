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

### Current molochs in this repo:

```json
{
  "data": {
    "factories": [
      {
        "moloch": "0x278ee41bf97e0e1aada301b459f12cea79503bd5",
        "title": "Macaw DAO"
      },
      {
        "moloch": "0x77b53ad9d111029d1f16f4f19769846384bda49b",
        "title": "James DAO"
      },
      {
        "moloch": "0x7d1a4fc6df3b16eb894004a4586a29f39ba6d205",
        "title": " DAOsaka DAICO"
      },
      {
        "moloch": "0xcc7dcdb700eed457c8180406d7d699877f4eee24",
        "title": "TrojanDAO"
      },
      {
        "moloch": "0xf5dbdb4ead400702bdae82a91a14998a1aaccfba",
        "title": "Osaka Interface DAO"
      }
           {
        "moloch": "0xf5dbdb4ead400702bdae82a91a14998a1aaccfba",
        "title": "Osaka Interface DAO"
      },
      {
        "moloch": "0xbd6fa666fbb6fdeb4fc5eb36cdd5c87b069b24c1",
        "title": "Raid Guild"
      },
    ]
  }
}
```
