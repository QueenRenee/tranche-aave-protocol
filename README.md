## AaveProtocol usage on Ethereum Blockchain

a) deploy JTrancheDeployer and JAave contract and initialize them (JAave parameters: address _priceOracle, address _feesCollector, address _tranchesDepl)

b) call setAavePoolAddressProvider(address _aavePool)

c) set JAave address in jTranchesDeployer contract

    setAavePoolAddressProvider: 0x88757f2f99175387aB4C6a4b3067c77A695b0349 on Kovan

d) call addTrancheToProtocol(address _erc20Contract, string memory _nameA, string memory _symbolA, 
            string memory _nameB, string memory _symbolB, uint256 _fixedRpb, uint8 _underlyingDec) to set a new tranche set

    add ETH tranche: "0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE","0x87b1f4cf9BD63f7BBD3eE1aD04E8F52540349347","Eth Tranche A","ETA","Eth Tranche B","ETB", web3.utils.toWei("0.04", "ether"),"18"  ----> Please read note below here

    add DAI tranche: "0xFf795577d9AC8bD7D90Ee22b6C1703490b6512FD","0xdCf0aF9e59C002FA3AA091a46196b37530FD48a8","Dai tranche A","DTA","Dai Tranche B","DTB", web3.utils.toWei("0.03", "ether"),"18"

    add USDT tranche: "0x13512979ADE267AB5100878E2e0f485B568328a4","0xFF3c8bc103682FA918c954E84F5056aB4DD5189d","USDT tranche A","USDTA","USDT Tranche B","USDTB",web3.utils.toWei("0.125", "ether"),"6"

    add USDC tranche: "0xe22da380ee6B445bb8273C81944ADEB6E8450422","0xe12AFeC5aa12Cf614678f9bFeeB98cA9Bb95b5B0","USDC tranche A","USDCA","USDC Tranche B","USDCB",web3.utils.toWei("0.02", "ether"),"6"


Users can now call buy and redeem functions for tranche A & B tokens

Note: if ETH tranche is deployed, please deploy WETHGateway contract without a proxy, then set its address in JAave with setWETHGatewayAddress function.


## AaveProtocol usage on Polygon layer

Please be aware that everything relative to ETH on Polygon layer is related to MATIC (native coin)

JAave system addresses on Poligon layer:

PriceOracle: 0xfcd2D3eb750f6a175da792e376eE83cf6DfaC8B8 initialized (reduced size and functions)

FeesCollector: 0x43f4E1B07bf982b2E7F0651BB848fC1f08c2EE98 initialized

TranchesDeployer: 0x69F1eB9806AC04f103C18C42E5F6daFa65a93939 initialized

JAave: 0x768371B5cbC86B7C542F6164C9718b2870D045Dd initialized (https://explorer-mainnet.maticvigil.com/address/0x768371B5cbC86B7C542F6164C9718b2870D045Dd/contracts)

0) set JAave in TranchesDeployer: 
    
    0x768371B5cbC86B7C542F6164C9718b2870D045Dd

1) initialize JAave: 

    "0xfcd2D3eb750f6a175da792e376eE83cf6DfaC8B8","0x43f4E1B07bf982b2E7F0651BB848fC1f08c2EE98","0x69F1eB9806AC04f103C18C42E5F6daFa65a93939"

2) setAavePoolAddressProvider: 
    
    0xd05e3E715d945B59290df0ae8eF85c1BdB684744

3) WETHGateway constructor pars: 

    "0x0d500b1d8e8ef31e21c99d1db9a6444d3adf1270","0x768371B5cbC86B7C542F6164C9718b2870D045Dd"

4) WETHGateway: 
    
    0x51393789fcfABD660c6D01611a0455E35545E645

5) setWETHGatewayAddress: 

    0x51393789fcfABD660c6D01611a0455E35545E645

Tranches:

    add Matic tranche as #0: "0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE","0x8dF3aad3a84da6b69A4DA8aeC3eA40d9091B2Ac4","Matic Tranche A","MTA","Matic Tranche B","MTB","4000000000000000","18"

    add USDC tranche as #1: "0x2791bca1f2de4661ed88a30c99a7a9449aa84174","0x1a13f4ca1d028320a707d99520abfefca3998b7f","USDC tranche A","USDCA","USDC Tranche B","USDCB","30000000000000","6"

    add WMatic tranche as #2: "0x0d500b1d8e8ef31e21c99d1db9a6444d3adf1270","0x8dF3aad3a84da6b69A4DA8aeC3eA40d9091B2Ac4","WMatic Tranche A","WMTA","WMatic Tranche B","WMTB","4000000000000000","18"

    add USDT tranche as #3: "0xc2132d05d31c914a87c6611c10748aeb04b58e8f","0x60d55f02a771d515e077c9c2403a1ef324885cec","USDT tranche A","USDTA","USDT Tranche B","USDTB","300000000000000","6"

    add DAI tranche as #4: "0x8f3cf7ad23cd3cadbd9735aff958023239c6a063","0x27f8d03b3a2196956ed754badc28d73be8830a6e","Dai tranche A","DTA","Dai Tranche B","DTB","3000000000000000","18"

    add WBTC tranche as #5: "0x1bfd67037b42cf73acf2047067bd4f2c47d9bfd6","0x5c2ed810328349100a66b82b78a1791b101c9d61","WBtc tranche A","WBTA","WBtc Tranche B","WBTB","3000000000000000","8"



## Contracts Size (main contracts, no interfaces, no test contracts)
Limit is 24 KiB for single contract
<table>
    <thead>
      <tr>
        <th>Contract</th>
        <th>Size</th>
      </tr>
    </thead>
    <tbody>
        <tr>
            <td>JAave</td>
            <td><code>17.62 KiB</code></td>
        </tr>
        <tr>
            <td>JAaveStorage</td>
            <td><code>1.62 KiB</code></td>
        </tr>
        <tr>
            <td>JTrancheAToken</td>
            <td><code>7.71 KiB</code></td>
        </tr>
        <tr>
            <td>JTrancheBToken</td>
            <td><code>7.71 KiB</code></td>
        </tr>
        <tr>
            <td>JTranchesDeployer</td>
            <td><code>18.62 KiB</code></td>
        </tr>
        <tr>
            <td>WETHGateway</td>
            <td><code>2.72 KiB</code></td>
        </tr>
    </tbody>
  </table>
