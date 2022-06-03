# Delisted NFT is stuck on marketplace, how to get it back

As few collections has been delisted, there is possibility that "marketplace" smartcontract might have ownership of NFT's that has been listed on marketplace (to sale)
In this situation user kinda lack possibility to unlist/cancel order that NFT from marketplace directly from website (due to delistning)

So lets figureout how to do it by interacting with blockchain

Marketplace contract address: `terra1fj44gmt0rtphu623zxge7u3t85qy0jg6p5ucnk`

- See list of collections [here](./marketplace-collections.md)

## Interact with Marketplace contract

1. Go to [TerraFinder](https://finder.terra.money)
1. Select chain (right to corner): __Classic__
1. Search for contract `terra1fj44gmt0rtphu623zxge7u3t85qy0jg6p5ucnk`
1. Or use direct link: [TerraFinder](https://finder.terra.money/classic/address/terra1fj44gmt0rtphu623zxge7u3t85qy0jg6p5ucnk)
1. Then you can execute queries

### Unlist NFT from marketplace - and send it back to owner

Marketplace contract have possibility to cancel offer (this would get you back your NFT)

```json
{
  "cancel_order": {
    "order_id": "<your _order_id>",
  }
}
```

_Note: Problem with it, is you gotta know order ID, and for do that, check other queries_

#### As you have `order_id`, execute it

Here is an example from [terra documentation](https://docs.terra.money/docs/develop/terra-js/smart-contracts.html#execute-a-contract), how to execute contract (remember, you have to configure account that have is order_creator)

```javascript
import { LCDClient, MsgExecuteContract, MnemonicKey } from '@terra-money/terra.js';

const terra = new LCDClient({
  URL: "https://columbus-lcd.terra.dev",
  chainId: "columbus-5",
});

const mnemonic = "needs-to-be-set";
const orderId = "sell_1654247688631_0.4068482569517984";

const mk = new MnemonicKey({ mnemonic: mnemonic });
const wallet = terra.wallet(mk);
const marketplaceAddress = 'terra1fj44gmt0rtphu623zxge7u3t85qy0jg6p5ucnk';

const execute = new MsgExecuteContract(
  wallet.key.accAddress, // sender address
  marketplaceAddress,   // contract account address
  {
    "cancel_order": {
      "order_id": orderId,
    }
  },
);

const executeTx = await wallet.createAndSignTx({
  msgs: [execute]
});

const executeTxResult = await terra.tx.broadcast(executeTx);


console.log({ sendMsgTxResult });
```

How to use it:
1. follow guide [Get started with Terra.js](https://docs.terra.money/docs/develop/terra-js/getting-started.html#get-started-with-terra-js), section "1. Set up your project)
1. you should have file `index.js`, so paste code from snippet above to that file
1. update in code, mnemonic and orderId variables
1. execute it with command: `node cancel_order.js`

### Get offers for collection (if you dont have token ID)

> This way you can directly on chain search for offers. It would allow you search offers and token_id

Query
```json
{
  "nft_tokens": {
    "nft_contract_address": "terra1trn7mhgc9e2wfkm5mhr65p3eu7a2lc526uwny2", // LunaBulls address for example
    "denom": "uluna", // or "uusd"
    "sort": "listing_time_newest", // Possible value: "price_highest", "price_lowest", "listing_time_newest", "listing_time_oldest"
    "limit": 30,
    "offset": "...." // optional
  }
}
```

_Note: remove commends in order to execute query_

### Get offers for collection (if you have token ID)

Lets say we have this NFT: https://marketplace.luart.io/collections/terra10f6n78sx84937kcqrthf2gkfxgfjgmxpqrlug7/3015

so nft_contract_address: `terra10f6n78sx84937kcqrthf2gkfxgfjgmxpqrlug7`
so token_id: `3015`

Query
```json
{
  "orders_for_token": {
    "nft_contract_address": "terra10f6n78sx84937kcqrthf2gkfxgfjgmxpqrlug7",
    "token_id": "3015",
    "limit": 30,
    "only_active": true
  }
}
```

_Note: remove commends in order to execute query_

And now you have:
```json
"order_id": "sell_1654247688631_0.4068482569517984",
"order_creator": "terra186l9tuzqhhjdmwhvmp59mzy2d3sn86q7fln49k",
```

### Get offers for user (if you know owner address)

For example lets use Terrans collection, with Address: `terra10f6n78sx84937kcqrthf2gkfxgfjgmxpqrlug7` (https://marketplace.luart.io/collections/terra10f6n78sx84937kcqrthf2gkfxgfjgmxpqrlug7)

Query
```json
{
  "orders_for_user": {
    "address": "terra186l9tuzqhhjdmwhvmp59mzy2d3sn86q7fln49k",
    "nft_contract_address": "terra10f6n78sx84937kcqrthf2gkfxgfjgmxpqrlug7", // optional, but lets use Terrans
    "limit": 30,
    "offset": "....", // optional
  }
}
```

This way you find out `order_id`, ex `sell_1654247688631_0.4068482569517984`, and could proceed with cancelation