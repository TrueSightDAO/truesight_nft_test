Example on how to create your own Candy Machine Page
====

- Over all instructions
  - Creating your Candy Machine: https://www.youtube.com/watch?v=inG53fpi_Lo
  - Creating your NFT assets: https://www.youtube.com/watch?v=6EEWFSvxFfs

- Pre-requisites:
  - Solana CLI
  - NodeJS: v14.7.5

- Install NodeJS -  https://github.com/garyjob/Setup-Wiki/blob/master/nodejs


- Install ts-node
  ```
  npm install -g ts-node
  ```

- Install yarn
  ```
  npm install -g yarn
  ```


- Install solana CLI: https://github.com/garyjob/Setup-Wiki/blob/master/solana.md

- Install Metaplex CLI: 
  ```
    $ git clone https://github.com/metaplex-foundation/metaplex.git
    $ cd metaplex
    $ cd js
    $ yarn install
    $ yarn bootstrap
    $ yarn start
  ```

- Configurate Solana Cli to DevNet for testing purposes
  ```
  solana config set --url https://api.devnet.solana.com
  ```

- Preparing the configuration file for the candy machine V2 - https://docs.metaplex.com/candy-machine-v2/configuration
  ```
  {
      "price": 1.5,
      "number": 1500,
      "gatekeeper": null,
      "solTreasuryAccount": "<<YOUR WALLET ADDRESS>>",
      "splTokenAccount": null,
      "splToken": null,
      "goLiveDate": "25 Dec 2021 00:00:00 GMT",
      "endSettings": null,
      "whitelistMintSettings": null,
      "hiddenSettings": null,
      "storage": "arweave-sol",
      "ipfsInfuraProjectId": null,
      "ipfsInfuraSecret": null,
      "nftStorageKey": null,
      "awsS3Bucket": null,
      "noRetainAuthority": false,
      "noMutable": false
  }
  ```

- Preparing your Asset - https://docs.metaplex.com/candy-machine-v2/preparing-assets
  ```
  {
      "name": "Number #0001",
      "symbol": "NB",
      "description": "Collection of 10 numbers on the blockchain. This is the number 1/10.",
      "seller_fee_basis_points": 500,
      "image": "0.png",
      "attributes": [
          {"trait_type": "Layer-1", "value": "0"},
          {"trait_type": "Layer-2", "value": "0"}, 
          {"trait_type": "Layer-3", "value": "0"},
          {"trait_type": "Layer-4", "value": "1"}
      ],
      "properties": {
          "creators": [{"address": "7fHHgY6Rpx63ancGYJKUgtQ6JdzQ3SuLj991KvqHmZu5", "share": 100}],
          "files": [{"uri": "0.png", "type": "image/png"}]
      },
      "collection": {"name": "numbers", "family": "numbers"}
  }  
  ```

- Uploading the NFT - https://docs.metaplex.com/candy-machine-v2/creating-candy-machine
  ```
  ts-node /Users/garyjob/Applications/truesight_nfts/metaplex/js/packages/cli/src/candy-machine-v2-cli.ts upload \
    -e devnet \
    -k /Users/garyjob/.config/solana/id.json \
    -cp config.json \
    /Users/garyjob/Applications/truesight_nfts/assets
  ```

- Verifying that NFT was Uploaded the NFT - https://docs.metaplex.com/candy-machine-v2/creating-candy-machine
  ```
  ts-node /Users/garyjob/Applications/truesight_nfts/metaplex/js/packages/cli/src/candy-machine-v2-cli.ts verify_upload \
    -e devnet \
    -k /Users/garyjob/.config/solana/id.json
  ```

- Minting One Token - https://docs.metaplex.com/candy-machine-v2/creating-candy-machine
  ```
  ts-node /Users/garyjob/Applications/truesight_nfts/metaplex/js/packages/cli/src/candy-machine-v2-cli.ts mint_one_token \
    -e devnet \
    -k /Users/garyjob/.config/solana/id.json
  ```

- Creating the Candy Machine UI
  - configuration in the metaplex repository
    ```
    cd js/packages/candy-machine-ui
    mv .env.example .env.example

    # Replace the line in this file to 
    REACT_APP_CANDY_MACHINE_ID=<YOUR CANDY MACHINE PROGRAM ID>

    # Replace the line in this file to 
    REACT_APP_CANDY_MACHINE_ID=3oH7gZ1DK7i9RJG91sfyB5829x6g84Mim4jabjf4F2mg    
    ```

- Resetting the project
  ```
  rm -rf .cache
  ```


-  Address the NFT was minted at on the Dev Net
  ```
  3oH7gZ1DK7i9RJG91sfyB5829x6g84Mim4jabjf4F2mg
  ```

