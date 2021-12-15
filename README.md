# first steps with TheGraph

An example of how to get started with The Graph using Hosted Service and the Gravatar smart contract

### 1. Install the Graph CLI

```
NPM
$ npm install -g @graphprotocol/graph-cli
```

### 2. Initialize your Subgraph

Initialize your subgraph from an existing contract.

```
$ graph init --product hosted-service --from-contract <Address>
```

```
$ graph init --product hosted-service --from-example
✔ Protocol · ethereum
✔ Subgraph name · luisvid/subgraphtest
✔ Directory to create the subgraph in · subgraphtest
———
✔ Cloning example subgraph
✔ Update subgraph name and commands in package.json
✔ Initialize subgraph repository
✔ Install dependencies with yarn
✔ Generate ABI and schema types with yarn codegen

Subgraph luisvid/subgraphtest created in subgraphtest
```

In the case of the example, the subgraph is based on the Gravity contract by Dani Grant that manages user avatars and emits NewGravatar or UpdateGravatar events whenever avatars are created or updated.


### 3. Write your Subgraph
The previous command will have created a scaffold from where you can build your subgraph. When making changes to the subgraph, you will mainly work with three files:

- Manifest (subgraph.yaml) - The manifest defines what datasources your subgraph will index
- Schema (schema.graphql) - The GraphQL schema define what data you wish to retrieve from the subgraph
- AssemblyScript Mappings (mapping.ts) - This is the code that translates data from your datasources to the entities defined in the schema


### 4. Deploy your Subgraph

- Sign into the Hosted Service using your github account
- Click Add Subgraph and fill out the required information. Use the same subgraph name as in step 2.
- Run codegen in the subgraph folder

```
NPM
$ npm run codegen
```

Add your Access token and deploy your subgraph. The access token is found on your dashboard in the Hosted Service.

```
$ graph auth --product hosted-service <ACCESS_TOKEN>
$ graph deploy --product hosted-service luisvid/subgraphtest
```

```
✔ Load subgraph from subgraph.yaml
  Compile data source: Gravity => build/Gravity/Gravity.wasm
✔ Compile subgraph
  Copy schema file build/schema.graphql
  Write subgraph file build/Gravity/abis/Gravity.json
  Write subgraph manifest build/subgraph.yaml
✔ Write compiled subgraph to build/
  Add file to IPFS build/schema.graphql
                .. QmbSFRGGvHM7Cn8YSjDL41diDMxN4LQUDEMqaa5VVc5sC4
  Add file to IPFS build/Gravity/abis/Gravity.json
                .. QmajZTadknSpgsCWRz9fG6bXFHdpVXPMWpx9yMipz3VtMQ
  Add file to IPFS build/Gravity/Gravity.wasm
                .. QmbK8QL1GWmsdTsgFYawvxFCjLEFwBsPjMGWpeRh6yaXEk
✔ Upload subgraph to IPFS

Build completed: QmXfCx2FYrBhbm7WP8Mn5N6ERbY3jfKVqjntZZYmyNhPRy

Deployed to https://thegraph.com/explorer/subgraph/luisvid/subgraphtest

Subgraph endpoints:
Queries (HTTP):     https://api.thegraph.com/subgraphs/name/luisvid/subgraphtest
Subscriptions (WS): wss://api.thegraph.com/subgraphs/name/luisvid/subgraphtest
```

### 5. Check your logs
.

### 6. Query your Subgraph

Sample query:

```
{
  gravatars(first: 5) {
    id
    owner
    displayName
    imageUrl
  }
}
```

![image](https://user-images.githubusercontent.com/330947/145645990-bc11403a-c34a-45e7-bc25-55e5d525b33b.png)


### For more information 

- see the docs on https://thegraph.com/docs/developer/quick-start#hosted-service.
- For great and real examples https://github.com/SimpleFi-finance/subgraphs

 \
 \
 
**Have fun! 😀
Let's #BUIDL 🚀**

![BUIDL_Logo_White](https://user-images.githubusercontent.com/330947/145646882-9319ba26-b56e-41c5-a790-a98f771768de.png)


