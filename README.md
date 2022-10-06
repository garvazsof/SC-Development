# SC-Development

Smart Contracts Development Guide

## Environment Configuration

1. Install [Metamask](https://metamask.io/) for your browser
2. Connect Metamask wallet to the Goerli testnet
    Name:               Goerli test network
    New RPC URL:        https://goerli.infura.io/v3/
    Chain ID:           5
    Currency symbol:    GoerliETH
    Block explorer URL: https://goerli.etherscan.io
    Visit [RPC Info](https://rpc.info/) if you want to connect to other networks.
3. Install [NodeJS LTS](https://nodejs.org/es/download/)
4. Install [Hardhat](https://hardhat.org/getting-started/)
5. Install [Truffle](https://trufflesuite.com/docs/truffle/getting-started/installation.html) 
6. Create a Github [github](https://github.com/)
7. Install [Visual Studio Code](https://code.visualstudio.com/download)
8. Install [remixd](https://www.npmjs.com/package/@remix-project/remixd)
9. Install [IPFS Desktop](https://github.com/ipfs/ipfs-desktop/releases)
10. Create an account [NFT.Storage] and get the API Key
11. If you prefer, you can create an account at [Pinata Cloud](https://www.pinata.cloud/)

# Tools

* [Remix](https://remix.ethereum.org/)
* [OpenZeppelin](https://docs.openzeppelin.com/contracts/4.x/) Tokens Docs 4.x
* [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/tree/release-v4.2/contracts/token) Tokens Github
* [Solidity](https://docs.soliditylang.org/en/v0.8.10/introduction-to-smart-contracts.html) 
* [OpenSea Testnet](https://testnets.opensea.io/)
* [Contracts Wizard](https://wizard.openzeppelin.com/)

# Creating Contrats

Please create a new npm application with npm init -y

1. Install Hardhat
    ``` 
        npm install --save-dev hardhat
    ``` 

2. Initialize Hardhat repo
    ``` 
        npx hardhat
    ```

    ``` 
        npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers @nomicfoundation/hardhat-toolbox
    ``` 

3. Install Openzeppelin dependencies

    ``` 
        npm install @openzeppelin/contracts
    ``` 
4. Compile the contracts

    ``` 
        npx hardhat compile
    ``` 

5. Test the contracts
    ``` 
        npx hardhat test
    ``` 

6. Deploy the contract
    ``` 
        npx hardhat run scripts/sample-script.js
    ``` 

7. Integrate to Remix IDE

    ``` 
        remixd -s ./ -u https://remix.ethereum.org
    ``` 

## Application to mint NFTs

1. Create a new application in a new folder

    ``` 
        npx create-react-app my-tokens-front
    ``` 

2. Test the new app

    ``` 
        cd nft-collectible-frontend
        npm start
    ``` 

3. Create a new contracts' folder in the src folder of the new app
4. Add contract's ABI in a new file named myNFTToken.json
5. Install Ethers.js
``` 
    npm install --save ethers
``` 

5. Replace the content of the app.js adding this code:

    ``` javascript
    import { useEffect, useState } from 'react';
    import './App.css';
    import contract from './contracts/NFTCollectible.json';
    import { ethers } from 'ethers';

    const contractAddress = "0x355638a4eCcb777794257f22f50c289d4189F245";
    const abi = contract.abi;

    function App() {

    const [currentAccount, setCurrentAccount] = useState(null);

    const checkWalletIsConnected = async () => {
        const { ethereum } = window;

        if (!ethereum) {
        console.log("Make sure you have Metamask installed!");
        return;
        } else {
        console.log("Wallet exists! We're ready to go!")
        }

        const accounts = await ethereum.request({ method: 'eth_accounts' });

        if (accounts.length !== 0) {
        const account = accounts[0];
        console.log("Found an authorized account: ", account);
        setCurrentAccount(account);
        } else {
        console.log("No authorized account found");
        }
    }

    const connectWalletHandler = async () => {
        const { ethereum } = window;

        if (!ethereum) {
        alert("Please install Metamask!");
        }

        try {
        const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
        console.log("Found an account! Address: ", accounts[0]);
        setCurrentAccount(accounts[0]);
        } catch (err) {
        console.log(err)
        }
    }

    const mintNftHandler = async () => {
        try {
        const { ethereum } = window;

        if (ethereum) {
            const provider = new ethers.providers.Web3Provider(ethereum);
            const signer = provider.getSigner();
            const nftContract = new ethers.Contract(contractAddress, abi, signer);

            console.log("Initialize payment");
            let nftTxn = await nftContract.mintNFTs(1, { value: ethers.utils.parseEther("0.01") });

            console.log("Mining... please wait");
            await nftTxn.wait();

            console.log(`Mined, see transaction: https://goerli.etherscan.io/tx/${nftTxn.hash}`);

        } else {
            console.log("Ethereum object does not exist");
        }

        } catch (err) {
        console.log(err);
        }
    }

    const connectWalletButton = () => {
        return (
        <button onClick={connectWalletHandler} className='cta-button connect-wallet-button'>
            Connect Wallet
        </button>
        )
    }

    const mintNftButton = () => {
        return (
        <button onClick={mintNftHandler} className='cta-button mint-nft-button'>
            Mint NFT
        </button>
        )
    }

    useEffect(() => {
        checkWalletIsConnected();
    }, [])

    return (
        <div className='main-app'>
        <h1>NFT Minting Tutorial</h1>
        <div>
            {currentAccount ? mintNftButton() : connectWalletButton()}
        </div>
        </div>
    )
    }

    export default App;
    ``` 
6. Replace App.css:

    ``` css
        .main-app {
        text-align: center;
        margin: 100px;
    }

    .cta-button {
        padding: 15px;
        border: none;
        border-radius: 12px;
        min-width: 250px;
        color: white;
        font-size: 18px;
        cursor: pointer;
    }

    .connect-wallet-button {
        background: rgb(32, 129, 226);
    }

    .mint-nft-button {
        background: orange;
    }

    ``` 
