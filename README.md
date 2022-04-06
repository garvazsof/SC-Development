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

## Aplicacion para mintear NFTs

