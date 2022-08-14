# 科学家极速抢NFT工具

以这个NFT发售为例 https://etherscan.io/address/0x984f7b398d577c0adde08293a53ae9d3b6b7a5c5

虽然没个NFT的合约不一样，但是抢NFT的基本原理都是一样的，你只需要修改几个配置就可以轻松使用这个工具。

# 工具使用环境：
1 Nodejs.v14 以上
2 免费申请一个Alchemy wss api

注意：Alchemy支持ETH和Polygon，其他公链需要用另外的api和调用方法，不懂的朋友通过最底下的电报联系我

# 如何配置

## 文件名：config.js

    // required. wallet privateKey, you can find it in your metamask
    privateKey : "<Your private key>",
    
    // required. Your wallet address   
    fromAddress : "<Your wallet address>".toLocaleLowerCase(),
    
    // reuiqred. Your target contract address
    toAddress: "<Your target contract address>".toLocaleLowerCase(),

    // required. Find out the contract creator address
    creatorAddress: "<The creator wallet address>".toLocaleLowerCase(),

    // required. The price of public mint. It should based on the smart contract
    price: "0.08",                    
    
    // required. How many items you wants to buy
    maxPriorityFeePerGas : "200", 
    
    // required. The collection contract address you want to buy                                                                           
    maxFeePerGas : "300",                    
    
    // required. The num you want to mint
    number: "1",

    // required. http provider from alchemy. It must be wss
    wssMainnet: "wss://eth-mainnet.alchemyapi.io/v2/<mainnet api key>",

    // required. http provider from alchemy. It must be wss
    wssRinkeby: "wss://eth-rinkeby.alchemyapi.io/v2/<Rinkeby api key>",

    // required. http provider from alchemy. It must be wss
    wssGoerli : "wss://eth-goerli.alchemyapi.io/v2/<Goerli api key>",

    // optional. debug usage. The value should be "Rinkeby" for rinkeby, "Goerli" for goerli or "" for mainnet
    network : "Goerli"

## 文件名：public.js, 只需要修改2个地方:

    1. 修改Mint的函数名
    本案例为：mintSAC
  
    //-----------------------------------------------------------------
    //--------------- Change this function every time------------------
  
    let extraData =  await contract.methods.mintSAC(config.number);
  
    //-----------------------------------------------------------------
    //-----------------------------------------------------------------
  
    2. 更改要监视的信号
    本案例为：flipPublicSaleState，当监测到智能合约有这个动作，立即发出交易
  
    //-----------------------------------------------------------------
    //--------------- Change this function every time------------------
  
    if((decodedData.name == 'flipPublicSaleState')){
  
    //-----------------------------------------------------------------
    //-----------------------------------------------------------------
  
## 文件名：abi.json

    你需要从智能合约中复制abi，并粘贴替换原有abi.json中的内容。 

# 所有隐私信息都存储在您的本地工作区中。Mint NFT不会发送任何个人信息或私钥。


