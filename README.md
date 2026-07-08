# Sablier Legacy Subgraph

This is the subgraph of the Sablier Legacy token streaming protocol. The most recent release is called Lockup and can be found [here](https://github.com/sablier-labs/lockup). For more details about how Sablier works, check out our docs at [docs.sablier.com](https://docs.sablier.com)/.

You can interact with the subgraph using The Graph Gateway:

- mainnet: `https://gateway-arbitrum.network.thegraph.com/api/<THE_GRAPH_API_KEY>/subgraphs/id/DkSXWkgJD5qVqfsrfzkLC5WELVX3Dbj3ByWcYjDJieCh`
- arbitrum: `https://gateway-arbitrum.network.thegraph.com/api/<THE_GRAPH_API_KEY>/subgraphs/id/94SP9QVcxmGV9e2fxuTxUGcZfcv4tjpPCGyyPVyMfLP`
- avalanche: `https://gateway-arbitrum.network.thegraph.com/api/<THE_GRAPH_API_KEY>/subgraphs/id/DK2gHCprwVaytwzwb5fUrkFS9xy7wh66NX6AFcDzMyF9`
- bsc: `https://gateway-arbitrum.network.thegraph.com/api/<THE_GRAPH_API_KEY>/subgraphs/id/3Gyy7of99oBRqHcCMGJXpHw2xxxZgXxVmFPFR1vL6YhT`
- matic: `https://gateway-arbitrum.network.thegraph.com/api/<THE_GRAPH_API_KEY>/subgraphs/id/6UMNQfMeh3pV5Qmn2NDX2UKNeUk9kh4oZhzzzn5e8rSz`
- optimism: `https://gateway-arbitrum.network.thegraph.com/api/<THE_GRAPH_API_KEY>/subgraphs/id/BEnQbvBdXnohC1DpM9rSb47C1FbowK39HfPNCEHjgrBt`

## Queries

Below are a few ways to show how to query the Sablier Legacy subgraph for data. The queries show most of the information that
is queryable, but there are many other filtering options that can be used. Just check out the GraphQL API.

### Query All Streams

```graphql
{
  streams {
    id
    cancellation {
      recipientBalance
      timestamp
      txhash
    }
    deposit
    ratePerSecond
    recipient
    sender
    startTime
    stopTime
    timestamp
    token {
      id
      decimals
      name
      symbol
    }
    txs {
      id
      block
      event
      from
      timestamp
      to
    }
    withdrawals {
      id
      amount
    }
  }
}
```

### Query All Streams for a Particular User

You can do this with the [`where`](https://thegraph.com/docs/en/querying/graphql-api/#example-using-where) clause. Make sure that the user address is in lowercase:

```graphql
{
  streams(where: { sender: "0xcafe...beef" }) {
    id
  }
}
```

### Query All Transactions

```graphql
{
  transactions {
    id
    block
    event
    from
    stream {
      id
    }
    timestamp
    to
  }
}
```
