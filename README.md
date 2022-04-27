# NFT bridge contracts using Celer IM
Features:
- support existing NFT contracts via PegNFT
- support new multi-chain native NFT, deploy MCNNFT contract on multiple chains

## Deploy NFT Bridge contract
1. Get Celer IM message bus contract address from https://im-docs.celer.network/developer/contract-addresses-and-rpc-info
2. Deploy NFTBridge.sol and set msg bus address from step 1 in constructor

## Deploy PegNFT.sol
1. Get NFT Bridge address from above step
2. Deploy PegNFT.sol with original NFT's name/symbol and nft bridge address

## Deploy MCNNFT.sol
1. Similar to PegNFT, first get NFT Bridge address from above step
2. Deploy MCNNFT.sol with NFT's name/symbol and nft bridge address


## Setup NFT Bridge
NFT Bridge has 4 maps:
### 1. DestTxFee
Set for each destination chain id, how much executor fee needs to be paid in this chain's gas token

### 2. DestBridge
Set the NFT Bridge address on each chain

### 3. DestNFTAddr
First key is supported NFT address on this chain, value is another map and its key is dest chain id, value is NFT address on that chain

### 4. OrigNFT
Only used to support existing NFT, only set to true if the NFT address on this chain is the original NFT contract, so nft bridge is smart to use transfer, not burn/mint