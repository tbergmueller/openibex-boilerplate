# openibex-boilerplate
A boilerplate project using OpenIbex-Dependencies

## Getting started

```
npm install;

# Setup a localchain and spawn node at port 8545
cd utils/localchain; npm install ; npx hardhat compile ; npx hardhat node & ; npx hardhat run scripts/deployStack.ts --network localhost; cd ../../

# Initialize OpenIbex
yarn run oi init
```

- This will produce an output containing `[...] CoreDB at: /orbitdb/xxxxx [...]`
- Copy the address of the db to config.yaml at `database.address` and make sure to uncomment this line
- You're set to go

Now try to interact with the smart contract on localchain;

``` 
### Will return 0 (as it does not have any tokens yet)
yarn run oi exec eip155:31337/erc20:0x5FbDB2315678afecb367f032d93F642f64180aa3 balanceOf 0x6d4cc96bd9135c25cbcaa4d38a0b514798a60360

### Send 1234 tokens to address 0x6d4cc96bd9135c25cbcaa4d38a0b514798a60360 from alice (which is the signer)
yarn run oi exec eip155:31337/erc20:0x5FbDB2315678afecb367f032d93F642f64180aa3 --wallet=alice transfer 0x6d4cc96bd9135c25cbcaa4d38a0b514798a60360,1234

### The balance now reads as 1234
yarn run oi exec eip155:31337/erc20:0x5FbDB2315678afecb367f032d93F642f64180aa3 balanceOf 0x6d4cc96bd9135c25cbcaa4d38a0b514798a60360
``` 

Congratulations, you've executed blockain transactions and read data from the blockchain. To build up an index, you can start listening to a smart contract`s events:

```
yarn run oi connect eip155:31337/erc20:0x5FbDB2315678afecb367f032d93F642f64180aa3
``` 

You already see the previous transaction and whenever you do a new transaction, you'll get a notification here.