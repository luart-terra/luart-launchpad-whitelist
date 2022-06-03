# How to find out collections on marketplace

So you are intrested in obtaining cetrain collection name/address or details

Marketplace contract address: `terra1fj44gmt0rtphu623zxge7u3t85qy0jg6p5ucnk`

## Interact with Marketplace contract

1. Go to [TerraFinder](https://finder.terra.money)
1. Select chain (right to corner): __Classic__
1. Search for contract `terra1fj44gmt0rtphu623zxge7u3t85qy0jg6p5ucnk`
1. Or use direct link: [TerraFinder](https://finder.terra.money/classic/address/terra1fj44gmt0rtphu623zxge7u3t85qy0jg6p5ucnk)
1. Then you can execute queries

### Available collections on marketplace

1. Click __Query__ to contract
1. Paste queru to form:
    ```json
    {
      "registered_nft_collections": {
        "limit": 5
      }
    }
    ```
1. Click Next
1. Then you should see Query result like below

    ```json
    {
      "nft_collections": [
        {
          "nft_contract_address": "terra103z9cnqm8psy0nyxqtugg6m7xnwvlkqdzm4s4k",
          "royalty_recipient": "terra1qzpww3mw0t9aep0x6ksf7nfsvhk3tjy7xt65g7"
        },
        {
          "nft_contract_address": "terra10f6n78sx84937kcqrthf2gkfxgfjgmxpqrlug7",
          "royalty_recipient": "terra15csx5yvcrg2rcvm8f7e8q6kl04p0zqxk4e4yue"
        },
        {
          "nft_contract_address": "terra10plsnuw2f3d8gnd8tp3de6hryyak2ntuhqcw97",
          "royalty_recipient": "terra18atq3jq6usqk379gkrec65ukqx8xpa7esnw3nt"
        },
        {
          "nft_contract_address": "terra10pxt36lyy6rhsumw7j8lahwvwrre7fxrfktgjl",
          "royalty_recipient": "terra1ea3vs4zqq7rmwzxkj05mv2v5nrq6az8rsu0kpl"
        },
        {
          "nft_contract_address": "terra10usryjgqcaylunrwp9eulgxz5j2zd40u2hxsc9",
          "royalty_recipient": "terra1sezshwv3262a7gve02rww20p5sly6esalcerma"
        }
      ],
      "offset": "terra10usryjgqcaylunrwp9eulgxz5j2zd40u2hxsc9"
    }
    ```

1. As you can see, response was limited to 5 records and there is another property offset, so lets execute another query to get next 5 collections
    ```json
    {
      "registered_nft_collections": {
        "limit": 5,
        "offset": "terra10usryjgqcaylunrwp9eulgxz5j2zd40u2hxsc9"
      }
    }
    ```
1. And this way you can obtain all 93 collections avaiable (max limit is 30)

### Collection details

1. Pick up one collection address as example, lets say `terra13fz4lrx6z952phcjjqzzacavnhxq2u5vt402vj`
1. Find that contract in [TerraFinder](https://finder.terra.money/classic/address/terra13fz4lrx6z952phcjjqzzacavnhxq2u5vt402vj)

### List of delisted collections on marketplace

Little bit more coinvinient version

| Title | Address |
|-------------|-------------|
| Metaracers | [terra1n8q524mu72wjfsayvhy2t2hjkkpa8nn6yzsedp](https://finder.terra.money/classic/address/terra1n8q524mu72wjfsayvhy2t2hjkkpa8nn6yzsedp) |
| Terra Turtles | [terra1sc89k9200ycvpd0cs0ul0qmj98p9n8wjp5sft7](https://finder.terra.money/classic/address/terra1sc89k9200ycvpd0cs0ul0qmj98p9n8wjp5sft7) |
| Space Cartels | [terra19relnlh7am0j9maggd4zdeed67v7jcm5k2clkr](https://finder.terra.money/classic/address/terra19relnlh7am0j9maggd4zdeed67v7jcm5k2clkr) |
| HellHounds | [terra1qz4ada96pqtxm0pg7gz4ttulv6cj7mjc4vdyl2](https://finder.terra.money/classic/address/terra1qz4ada96pqtxm0pg7gz4ttulv6cj7mjc4vdyl2) |
| HellCats | [terra1uv9w7aaq6lu2kn0asnvknlcgg2xd5ts57ss7qt](https://finder.terra.money/classic/address/terra1uv9w7aaq6lu2kn0asnvknlcgg2xd5ts57ss7qt) |
| LunaBulls | [terra1trn7mhgc9e2wfkm5mhr65p3eu7a2lc526uwny2](https://finder.terra.money/classic/address/terra1trn7mhgc9e2wfkm5mhr65p3eu7a2lc526uwny2) |
| LunaBulls 3D | [terra18d5cqlsqgxp8w7ysn48l4r8a5328592wfwjtyz](https://finder.terra.money/classic/address/terra18d5cqlsqgxp8w7ysn48l4r8a5328592wfwjtyz) |
| LunaBulls Tesseract | [terra1k5pa7htlznr7hskhr9dx8qlk65emhktrgmuknd](https://finder.terra.money/classic/address/terra1k5pa7htlznr7hskhr9dx8qlk65emhktrgmuknd) |
| BabyBulls | [terra1zvmesqul8ss2ty84eml8aqkq0kq5ydwjuyf6a3](https://finder.terra.money/classic/address/terra1zvmesqul8ss2ty84eml8aqkq0kq5ydwjuyf6a3) |
| RoboHero | [terra1pw0x4f7ktv4vdqvx8dfaa5d2lp0t5rpzep9ewn](https://finder.terra.money/classic/address/terra1pw0x4f7ktv4vdqvx8dfaa5d2lp0t5rpzep9ewn) |