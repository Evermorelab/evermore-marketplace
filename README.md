# Evermore marketplace

Evermore Marketplace uses NFT royalties to create revenue for consumer product companies from re-sales, incentivising them to design more durable products and decrease demand on new materials.

We are solving for sustainability being an incentives alignment problem. The current linear economy is defined by taking, making and wasting. Resources are extracted from the earth to produce products, which are sold to customers for consumption and once irrelevant, products are disposed of. 

## Features

- Buy new products from our selected merchants and get the corresponding NFT
- Buy 2nd hand products from other users
- Check your products on My Items page
- When you do not need a product anymore, re-list it for sale with one click from My Items page
- Cancel your listing anytime

## Prerequisites


- The project runs on XDC testnet apothem. If you don't have this network in your metamask wallet, please follow this [tutorial](https://docs.xdc.community/get-details/wallet-integration/metamask#-adding-xdc-mainnet-and-apothem-testnet-in-metamask)
- Get some TXDC from XDC Apothem Faucet: https://faucet.apothem.network/

Checkout our demo: https://63bc3f4d46a4a820b75d73d1--moonlit-semifreddo-529df1.netlify.app/

## Project

This project contains submodules, to clone it use:
`git clone --recurse-submodules https://github.com/flo-3/evermore-marketplace.git`

Follow the installation steps in each folder.

The marketplace consists of:
- 2 solidity smart contracts: EvermoreMarketplace and EvermoreNFT in `evermore-marketplace-solidity-sc` folder
- a NextJS interface in `evermore-marketplace-frontend` folder
- a demo database that you can find here: https://docs.google.com/spreadsheets/d/1oNu2ya8MO9qkhDaRfmZzO5_tT63uVM5u46e8HREadlM/edit?usp=sharing

## Deploy

#### Deploy the marketplace

1. Deploy the marketplace SC using `npx hardhat run scripts/deployCollection.js --network apothem` in `evermore-marketplace-solidity-sc` and add the contract address into the frontend .env.local file. Setup fees receipient.

#### Deploy a new collection
=> This process will be replaced by a management interface for merchants to easily upload their products
1. For each products collection you want to sell on the marketplace, create a line in the database with all the values. Make sure to have one uids per product; this is the unique identifier that is associated to the physical product.
2. Deploy each products collection smart contract using `npx hardhat run scripts/deployCollection.js --network apothem` in `evermore-marketplace-solidity-sc` and add its smart contract address into the database
3. Upload the collection on IPFS (button avalaible on the front interface) and the CID in the database in product_base_uri and in the corresponding smart contract using `setbaseURI` function (important, you can't mint a product without this baseURI)
4. Setup the fees recipient and the royalties recipient


## Upcoming features
- Style fix: user dropdown, products & categories grid fix, error & success display
- Better handle to conversion between displayed FIAT prices and XDC token for payement
- Shipment feature + escrow: when a user buys a product, they will have to give their address so they can receive the product. An escorw feature will be implemented in the smart contract to hold the NFT and the payment until the buyer confirms the product reception.
- Web2 friendly: add connector for a wallet accessible from an email address, so even users withtout any web3 knowledge will be able to use the marketplace
- Product timeline: a buyer will see the entire product history with its condition and price
- UX and UI enhancements
- Control the resale price and update it anytime
- Whithdraw the money earned on the marketplace into your wallet
- Upload product interface: to automatize the collection creation

