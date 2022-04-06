# SC-Development
Repositorio para curso de desarrollo de contratos inteligentes

## Configuracion del entorno

1. Empezamos instalando la Wallet [Metamask](https://metamask.io/) para nuestro navegador
2. Conectamos la wallet a la red Ropsten o Rinkeby y obtenemos ETH de prueba desde la faucet de [Rinkeby](https://faucet.rinkeby.io/) o de [Ropsten](https://faucet.metamask.io/)
3. Instalamos [NodeJS LTS](https://nodejs.org/es/download/)
4. Instalamos la utilería [Hardhat](https://hardhat.org/getting-started/)
5. Instalamos la utilería [Truffle](https://trufflesuite.com/docs/truffle/getting-started/installation.html) 
6. Creamos una cuenta en [github](https://github.com/)
7. Instalamos [Visual Studio Code](https://code.visualstudio.com/download)
8. Instalar [remixd](https://www.npmjs.com/package/@remix-project/remixd)
9. Instalamos [IPFS Desktop](https://github.com/ipfs/ipfs-desktop/releases)
10. Creamos una cuenta en [NFT.Storage] y obtenemos el API Key 
11. De manera opcional creamos una cuenta en [Pinata Cloud](https://www.pinata.cloud/)

# Links de Herramientas

* [Remix](https://remix.ethereum.org/)
* [OpenZeppelin](https://docs.openzeppelin.com/contracts/4.x/) Tokens Docs 4.x
* [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/tree/release-v4.2/contracts/token) Tokens Github
* [Solidity](https://docs.soliditylang.org/en/v0.8.10/introduction-to-smart-contracts.html) 
* 
# Creacion de Contratos

1. Instalar Hardhat
    ``` 
        npm install --save-dev hardhat
    ``` 

2. Inicializar el repo con Hardhat
    ``` 
        npx hardhat
    ```

    ``` 
        npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers
    ``` 

3. Compilar los contratos

    ``` 
        npx hardhat compile
    ``` 

4. Probar los contratos
    ``` 
        npx hardhat test
    ``` 

5. Hacer deploy del contrato
    ``` 
        npx hardhat run scripts/sample-script.js
    ``` 

6. Integrar con Remix IDE

    ``` 
        remixd -s ./ -u https://remix.ethereum.org
    ``` 

7. Instalar Openzeppelin

    ``` 
        npm install @openzeppelin/contracts
    ``` 

## Aplicacion para mintear NFTs

1. Crear la aplicación web

    ``` 
        npx create-react-app my-tokens-front
    ``` 

2. Probamos la nueva app

    ``` 
        cd nft-collectible-frontend
        npm start
    ``` 

3. Crear carpeta contracts en la carpeta src de la nueva app
4. Agregar el ABI del contrato en un nuevo archivo myNFTToken.json
5. Remplazar el contenido del archivo app.js por lo siguiente:
    ``` javascript
    import { useEffect } from 'react';
    import './App.css';
    import contract from './contracts/NFTCollectible.json';

    const contractAddress = "0x355638a4eCcb777794257f22f50c289d4189F245";
    const abi = contract.abi;

    function App() {

    const checkWalletIsConnected = () => { }

    const connectWalletHandler = () => { }

    const mintNftHandler = () => { }

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
        <h1>Scrappy Squirrels Tutorial</h1>
        <div>
            {connectWalletButton()}
        </div>
        </div>
    )
    }

    export default App;
    ``` 
6. Remplazar el contenido del archivo App.css:

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