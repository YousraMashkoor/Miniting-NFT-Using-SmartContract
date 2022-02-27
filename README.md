# **Minting NFT Using Smart Contact**

## Install Hardhat
```shell
mkdir elonNFT
cd elonNFT
npm init --yes 
npm install --save-dev hardhat
```

create a hardhat project
```
npx hardhat
```
install these dependencies, if not already
```
npm install --save-dev @nomiclabs/hardhat-ethers ethers @nomiclabs/hardhat-waffle ethereum-waffle chai
npm install @openzeppelin/contracts
```

## Creating ERC721 Contract
For minting NFTs, we will create a basic contract based on ERC721 - the non-fungible token standard. OpenZeppelin gives us the base ERC721 with all the important functionalities.   
Use OpenZappelin wizard [here](https://docs.openzeppelin.com/contracts/4.x/wizard) to create a contract

Goto https://jsonkeeper.com/ and create a jsonlink for your NFT properties, see the sample below:
```json
{    
    "name":"Elon Musk",
    "description":"Making inter planetory travel possible and pushing the boundaries for mankind.",
    "image":"https://www.linkpicture.com/q/Elon-Musk-with-Doge-web_1.jpg",
 
    "attributes":
    [
        {
            "trait_type":"Zodiac","value":"Cancer"
        },
        {
            "trait_type":"Height","value":"6'1"
        },
        {    "trait_type":"Personality Type","value":"INTJ"
        }
    ]
}
```
and give this json link to your **_setTokenURI** under contracts/ElonNFT.sol
```JS
_setTokenURI(tokenId, 'https://jsonkeeper.com/b/5BZ1');
```

## Blockchain Environment

select Rinkeby Testnet for deployment of this contact. Try the following websites and try to get some fake ETHs. This fake money will be used for deploying your contract and doing transactions on your contract.

All you have to do is to drop your public address on the following links and the ETH will be transferred.

https://faucets.chain.link/rinkeby  
https://rinkeby-faucet.com/


## Creating alchemy app
Alchemy gives you the ability to read and write on blockchain via their infrastructure. It saves you time. It saves you money and keeps things efficient. 

Sign up for your free account here https://dashboard.alchemyapi.io/ and create and app with following properties. 

Environment - Staging
Chain - Ethereum
Network - Rinkeby

## Setting Environment
```
npm install dotenv --save
touch .env
```
add these keys  

```
PRIVATE_KEY = YOUR-PRIVATE-KEY
API_URL_KEY = YOUR-ALCHEMY-APP-URL
API_KEY = YOUR-ALCHEMY-APP-KEY
```

## Deployment
Use this command to deploy your smart contract to Rinkeby Server
```
npx hardhat run scripts/run.js --network rinkeby
```