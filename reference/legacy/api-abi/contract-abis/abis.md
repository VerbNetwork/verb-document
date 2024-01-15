# ABIs

{% hint style="warning" %}
You are referring to the **`Legacy`** version of KyberSwap docs.

For the most updated information, please refer to:

* [**`Classic`**](../../../../liquidity-solutions/kyberswap-classic/)
* [**`Elastic`**](../../../../liquidity-solutions/kyberswap-elastic/)
* [**`Limit Order`**](../../../../kyberswap-solutions/limit-order/)
* [**`Aggregator`**](../../../../kyberswap-solutions/kyberswap-aggregator/)
{% endhint %}

The contract Application Binary Interface (ABI) is the standard way to interact with the smart contracts in Ethereum.

We recommend importing the interfaces for the following functionalities:

* [`IKyberNetworkProxy`](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikybernetworkproxy): Fetch rates and execute trades
* [`ISimpleKyberProxy`](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#isimplekyberproxy): Simple APIs for trade execution
* [`IKyberHint`](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberhint): Building and parsing hints
* [`IKyberStorage`](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberstorage): Get reserve IDs for building hints
* [`IKyberFeeHandler`](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberfeehandler): Claim staker rewards, reserve rebates or platform fees
* [`IKyberReserve`](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberreserve): Fetch rates of a specific reserve
* [`IERC20`](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ierc20): Token operations (Eg. token transfers / approvals)

The full contract ABIs are also given below the interface section.

### Interface ABIs[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#interface-abis) <a href="#interface-abis" id="interface-abis"></a>

#### `IKyberNetworkProxy`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikybernetworkproxy) <a href="#ikybernetworkproxy" id="ikybernetworkproxy"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/IKyberNetworkProxy.sol)

```
[
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'trader',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'contract IERC20',
        name: 'src',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'contract IERC20',
        name: 'dest',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'destAddress',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'actualSrcAmount',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'actualDestAmount',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'platformWallet',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'platformFeeBps',
        type: 'uint256',
      },
    ],
    name: 'ExecuteTrade',
    type: 'event',
  },
  {
    inputs: [
      { internalType: 'contract ERC20', name: 'src', type: 'address' },
      { internalType: 'contract ERC20', name: 'dest', type: 'address' },
      { internalType: 'uint256', name: 'srcQty', type: 'uint256' },
    ],
    name: 'getExpectedRate',
    outputs: [
      { internalType: 'uint256', name: 'expectedRate', type: 'uint256' },
      { internalType: 'uint256', name: 'worstRate', type: 'uint256' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'uint256', name: 'srcQty', type: 'uint256' },
      { internalType: 'uint256', name: 'platformFeeBps', type: 'uint256' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'getExpectedRateAfterFee',
    outputs: [
      { internalType: 'uint256', name: 'expectedRate', type: 'uint256' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'address payable', name: 'destAddress', type: 'address' },
      { internalType: 'uint256', name: 'maxDestAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
      {
        internalType: 'address payable',
        name: 'platformWallet',
        type: 'address',
      },
    ],
    name: 'trade',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract ERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract ERC20', name: 'dest', type: 'address' },
      { internalType: 'address payable', name: 'destAddress', type: 'address' },
      { internalType: 'uint256', name: 'maxDestAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
      { internalType: 'address payable', name: 'walletId', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'tradeWithHint',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'address payable', name: 'destAddress', type: 'address' },
      { internalType: 'uint256', name: 'maxDestAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
      {
        internalType: 'address payable',
        name: 'platformWallet',
        type: 'address',
      },
      { internalType: 'uint256', name: 'platformFeeBps', type: 'uint256' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'tradeWithHintAndFee',
    outputs: [{ internalType: 'uint256', name: 'destAmount', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
];
```

#### `ISimpleKyberProxy`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#isimplekyberproxy) <a href="#isimplekyberproxy" id="isimplekyberproxy"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/ISimpleKyberProxy.sol)

```
[
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapEtherToToken',
    outputs: [{ internalType: 'uint256', name: 'destAmount', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapTokenToEther',
    outputs: [{ internalType: 'uint256', name: 'destAmount', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapTokenToToken',
    outputs: [{ internalType: 'uint256', name: 'destAmount', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
];
```

#### `IKyberHint`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberhint) <a href="#ikyberhint" id="ikyberhint"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/IKyberHint.sol)

```
[
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    name: 'buildEthToTokenHint',
    outputs: [{ internalType: 'bytes', name: 'hint', type: 'bytes' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
    ],
    name: 'buildTokenToEthHint',
    outputs: [{ internalType: 'bytes', name: 'hint', type: 'bytes' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    name: 'buildTokenToTokenHint',
    outputs: [{ internalType: 'bytes', name: 'hint', type: 'bytes' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'parseEthToTokenHint',
    outputs: [
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'ethToTokenAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'parseTokenToEthHint',
    outputs: [
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'tokenToEthAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'parseTokenToTokenHint',
    outputs: [
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'tokenToEthAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'ethToTokenAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
];
```

#### `IKyberStorage`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberstorage) <a href="#ikyberstorage" id="ikyberstorage"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/IKyberStorage.sol)

```
[
  {
    inputs: [
      { internalType: 'address', name: 'kyberProxy', type: 'address' },
      { internalType: 'uint256', name: 'maxApprovedProxies', type: 'uint256' },
    ],
    name: 'addKyberProxy',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getEntitledRebateData',
    outputs: [
      { internalType: 'bool[]', name: 'entitledRebateArr', type: 'bool[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getFeeAccountedData',
    outputs: [
      { internalType: 'bool[]', name: 'feeAccountedArr', type: 'bool[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getKyberProxies',
    outputs: [
      {
        internalType: 'contract IKyberNetworkProxy[]',
        name: '',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getRebateWalletsFromIds',
    outputs: [
      { internalType: 'address[]', name: 'rebateWallets', type: 'address[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'bytes32', name: 'reserveId', type: 'bytes32' }],
    name: 'getReserveAddressesByReserveId',
    outputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getReserveAddressesFromIds',
    outputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'uint256', name: 'startIndex', type: 'uint256' },
      { internalType: 'uint256', name: 'endIndex', type: 'uint256' },
    ],
    name: 'getReserveAddressesPerTokenSrc',
    outputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'reserve', type: 'address' }],
    name: 'getReserveDetailsByAddress',
    outputs: [
      { internalType: 'bytes32', name: 'reserveId', type: 'bytes32' },
      { internalType: 'address', name: 'rebateWallet', type: 'address' },
      {
        internalType: 'enum IKyberStorage.ReserveType',
        name: 'resType',
        type: 'uint8',
      },
      { internalType: 'bool', name: 'isFeeAccountedFlag', type: 'bool' },
      { internalType: 'bool', name: 'isEntitledRebateFlag', type: 'bool' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'bytes32', name: 'reserveId', type: 'bytes32' }],
    name: 'getReserveDetailsById',
    outputs: [
      { internalType: 'address', name: 'reserveAddress', type: 'address' },
      { internalType: 'address', name: 'rebateWallet', type: 'address' },
      {
        internalType: 'enum IKyberStorage.ReserveType',
        name: 'resType',
        type: 'uint8',
      },
      { internalType: 'bool', name: 'isFeeAccountedFlag', type: 'bool' },
      { internalType: 'bool', name: 'isEntitledRebateFlag', type: 'bool' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'reserve', type: 'address' }],
    name: 'getReserveId',
    outputs: [{ internalType: 'bytes32', name: 'reserveId', type: 'bytes32' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    name: 'getReserveIdsFromAddresses',
    outputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
    ],
    name: 'getReserveIdsPerTokenDest',
    outputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
    ],
    name: 'getReserveIdsPerTokenSrc',
    outputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
    ],
    name: 'getReservesData',
    outputs: [
      { internalType: 'bool', name: 'areAllReservesListed', type: 'bool' },
      { internalType: 'bool[]', name: 'feeAccountedArr', type: 'bool[]' },
      { internalType: 'bool[]', name: 'entitledRebateArr', type: 'bool[]' },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'isKyberProxyAdded',
    outputs: [{ internalType: 'bool', name: '', type: 'bool' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'kyberProxy', type: 'address' }],
    name: 'removeKyberProxy',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: '_kyberFeeHandler', type: 'address' },
      {
        internalType: 'address',
        name: '_kyberMatchingEngine',
        type: 'address',
      },
    ],
    name: 'setContracts',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: '_kyberDao', type: 'address' }],
    name: 'setKyberDaoContract',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
];
```

#### `IKyberFeeHandler`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberfeehandler) <a href="#ikyberfeehandler" id="ikyberfeehandler"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/IKyberFeeHandler.sol)

```
[
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'uint256',
        name: 'kncTWei',
        type: 'uint256',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'KncBurned',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'platformWallet',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'PlatformFeePaid',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'rebateWallet',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'RebatePaid',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'staker',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'uint256',
        name: 'epoch',
        type: 'uint256',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'RewardPaid',
    type: 'event',
  },
  {
    inputs: [
      { internalType: 'address', name: 'platformWallet', type: 'address' },
    ],
    name: 'claimPlatformFee',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: 'rebateWallet', type: 'address' },
    ],
    name: 'claimReserveRebate',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: 'staker', type: 'address' },
      { internalType: 'uint256', name: 'epoch', type: 'uint256' },
    ],
    name: 'claimStakerReward',
    outputs: [{ internalType: 'uint256', name: 'amount', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'address[]', name: 'eligibleWallets', type: 'address[]' },
      {
        internalType: 'uint256[]',
        name: 'rebatePercentages',
        type: 'uint256[]',
      },
      { internalType: 'address', name: 'platformWallet', type: 'address' },
      { internalType: 'uint256', name: 'platformFee', type: 'uint256' },
      { internalType: 'uint256', name: 'networkFee', type: 'uint256' },
    ],
    name: 'handleFees',
    outputs: [],
    stateMutability: 'payable',
    type: 'function',
  },
];
```

#### `IKyberReserve`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ikyberreserve) <a href="#ikyberreserve" id="ikyberreserve"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/IKyberReserve.sol)

```
[
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'uint256', name: 'srcQty', type: 'uint256' },
      { internalType: 'uint256', name: 'blockNumber', type: 'uint256' },
    ],
    name: 'getConversionRate',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'srcToken', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract IERC20', name: 'destToken', type: 'address' },
      { internalType: 'address payable', name: 'destAddress', type: 'address' },
      { internalType: 'uint256', name: 'conversionRate', type: 'uint256' },
      { internalType: 'bool', name: 'validate', type: 'bool' },
    ],
    name: 'trade',
    outputs: [{ internalType: 'bool', name: '', type: 'bool' }],
    stateMutability: 'payable',
    type: 'function',
  },
];
```

#### `IERC20`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#ierc20) <a href="#ierc20" id="ierc20"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/IERC20.sol)

```
[
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: '_owner',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'address',
        name: '_spender',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: '_value',
        type: 'uint256',
      },
    ],
    name: 'Approval',
    type: 'event',
  },
  {
    inputs: [
      { internalType: 'address', name: '_owner', type: 'address' },
      { internalType: 'address', name: '_spender', type: 'address' },
    ],
    name: 'allowance',
    outputs: [{ internalType: 'uint256', name: 'remaining', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: '_spender', type: 'address' },
      { internalType: 'uint256', name: '_value', type: 'uint256' },
    ],
    name: 'approve',
    outputs: [{ internalType: 'bool', name: 'success', type: 'bool' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: '_owner', type: 'address' }],
    name: 'balanceOf',
    outputs: [{ internalType: 'uint256', name: 'balance', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'decimals',
    outputs: [{ internalType: 'uint8', name: 'digits', type: 'uint8' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'totalSupply',
    outputs: [{ internalType: 'uint256', name: 'supply', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: '_to', type: 'address' },
      { internalType: 'uint256', name: '_value', type: 'uint256' },
    ],
    name: 'transfer',
    outputs: [{ internalType: 'bool', name: 'success', type: 'bool' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: '_from', type: 'address' },
      { internalType: 'address', name: '_to', type: 'address' },
      { internalType: 'uint256', name: '_value', type: 'uint256' },
    ],
    name: 'transferFrom',
    outputs: [{ internalType: 'bool', name: 'success', type: 'bool' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
];
```

#### `KyberNetworkProxyInterface (V1)`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#kybernetworkproxyinterface-v1) <a href="#kybernetworkproxyinterface-v1" id="kybernetworkproxyinterface-v1"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol4/KyberNetworkProxyInterface.sol)

```
[
  {
    constant: true,
    inputs: [],
    name: 'enabled',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'srcAmount', type: 'uint256' },
      { name: 'dest', type: 'address' },
      { name: 'destAddress', type: 'address' },
      { name: 'maxDestAmount', type: 'uint256' },
      { name: 'minConversionRate', type: 'uint256' },
      { name: 'walletId', type: 'address' },
      { name: 'hint', type: 'bytes' },
    ],
    name: 'tradeWithHint',
    outputs: [{ name: '', type: 'uint256' }],
    payable: true,
    stateMutability: 'payable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'maxGasPrice',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'user', type: 'address' }],
    name: 'getUserCapInWei',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'dest', type: 'address' },
      { name: 'srcQty', type: 'uint256' },
    ],
    name: 'getExpectedRate',
    outputs: [
      { name: 'expectedRate', type: 'uint256' },
      { name: 'slippageRate', type: 'uint256' },
    ],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'user', type: 'address' },
      { name: 'token', type: 'address' },
    ],
    name: 'getUserCapInTokenWei',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'id', type: 'bytes32' }],
    name: 'info',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
];
```

#### `ConversionRatesInterface`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#conversionratesinterface) <a href="#conversionratesinterface" id="conversionratesinterface"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol4/ConversionRatesInterface.sol)

```
[
  {
    constant: true,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'currentBlockNumber', type: 'uint256' },
      { name: 'buy', type: 'bool' },
      { name: 'qty', type: 'uint256' },
    ],
    name: 'getRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'buyAmount', type: 'int256' },
      { name: 'rateUpdateBlock', type: 'uint256' },
      { name: 'currentBlock', type: 'uint256' },
    ],
    name: 'recordImbalance',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
];
```

#### `SanityRatesInterface`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#sanityratesinterface) <a href="#sanityratesinterface" id="sanityratesinterface"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol4/SanityRatesInterface.sol)

```
[
  {
    constant: true,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'dest', type: 'address' },
    ],
    name: 'getSanityRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
];
```

### Full Contract ABIs[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#full-contract-abis) <a href="#full-contract-abis" id="full-contract-abis"></a>

#### `KyberNetworkProxy V2 (Katalyst)`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#kybernetworkproxy-v2-katalyst) <a href="#kybernetworkproxy-v2-katalyst" id="kybernetworkproxy-v2-katalyst"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/KyberNetworkProxy.sol)

```
[
  {
    inputs: [{ internalType: 'address', name: '_admin', type: 'address' }],
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'newAdmin',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'previousAdmin',
        type: 'address',
      },
    ],
    name: 'AdminClaimed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'newAlerter',
        type: 'address',
      },
      { indexed: false, internalType: 'bool', name: 'isAdd', type: 'bool' },
    ],
    name: 'AlerterAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'sendTo',
        type: 'address',
      },
    ],
    name: 'EtherWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'trader',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'contract IERC20',
        name: 'src',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'contract IERC20',
        name: 'dest',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'destAddress',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'actualSrcAmount',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'actualDestAmount',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'platformWallet',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'platformFeeBps',
        type: 'uint256',
      },
    ],
    name: 'ExecuteTrade',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'contract IKyberHint',
        name: 'kyberHintHandler',
        type: 'address',
      },
    ],
    name: 'KyberHintHandlerSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'contract IKyberNetwork',
        name: 'newKyberNetwork',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'contract IKyberNetwork',
        name: 'previousKyberNetwork',
        type: 'address',
      },
    ],
    name: 'KyberNetworkSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'newOperator',
        type: 'address',
      },
      { indexed: false, internalType: 'bool', name: 'isAdd', type: 'bool' },
    ],
    name: 'OperatorAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'sendTo',
        type: 'address',
      },
    ],
    name: 'TokenWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'pendingAdmin',
        type: 'address',
      },
    ],
    name: 'TransferAdminPending',
    type: 'event',
  },
  {
    inputs: [{ internalType: 'address', name: 'newAlerter', type: 'address' }],
    name: 'addAlerter',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'newOperator', type: 'address' }],
    name: 'addOperator',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'admin',
    outputs: [{ internalType: 'address', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'claimAdmin',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'enabled',
    outputs: [{ internalType: 'bool', name: '', type: 'bool' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getAlerters',
    outputs: [{ internalType: 'address[]', name: '', type: 'address[]' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract ERC20', name: 'src', type: 'address' },
      { internalType: 'contract ERC20', name: 'dest', type: 'address' },
      { internalType: 'uint256', name: 'srcQty', type: 'uint256' },
    ],
    name: 'getExpectedRate',
    outputs: [
      { internalType: 'uint256', name: 'expectedRate', type: 'uint256' },
      { internalType: 'uint256', name: 'worstRate', type: 'uint256' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'uint256', name: 'srcQty', type: 'uint256' },
      { internalType: 'uint256', name: 'platformFeeBps', type: 'uint256' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'getExpectedRateAfterFee',
    outputs: [
      { internalType: 'uint256', name: 'expectedRate', type: 'uint256' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getOperators',
    outputs: [{ internalType: 'address[]', name: '', type: 'address[]' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberHintHandler',
    outputs: [
      { internalType: 'contract IKyberHint', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberNetwork',
    outputs: [
      { internalType: 'contract IKyberNetwork', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'maxGasPrice',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'pendingAdmin',
    outputs: [{ internalType: 'address', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'alerter', type: 'address' }],
    name: 'removeAlerter',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'operator', type: 'address' }],
    name: 'removeOperator',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'contract IKyberHint',
        name: '_kyberHintHandler',
        type: 'address',
      },
    ],
    name: 'setHintHandler',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'contract IKyberNetwork',
        name: '_kyberNetwork',
        type: 'address',
      },
    ],
    name: 'setKyberNetwork',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapEtherToToken',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapTokenToEther',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapTokenToToken',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'address payable', name: 'destAddress', type: 'address' },
      { internalType: 'uint256', name: 'maxDestAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
      {
        internalType: 'address payable',
        name: 'platformWallet',
        type: 'address',
      },
    ],
    name: 'trade',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract ERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract ERC20', name: 'dest', type: 'address' },
      { internalType: 'address payable', name: 'destAddress', type: 'address' },
      { internalType: 'uint256', name: 'maxDestAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
      { internalType: 'address payable', name: 'walletId', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'tradeWithHint',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'uint256', name: 'srcAmount', type: 'uint256' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
      { internalType: 'address payable', name: 'destAddress', type: 'address' },
      { internalType: 'uint256', name: 'maxDestAmount', type: 'uint256' },
      { internalType: 'uint256', name: 'minConversionRate', type: 'uint256' },
      {
        internalType: 'address payable',
        name: 'platformWallet',
        type: 'address',
      },
      { internalType: 'uint256', name: 'platformFeeBps', type: 'uint256' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'tradeWithHintAndFee',
    outputs: [{ internalType: 'uint256', name: 'destAmount', type: 'uint256' }],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'newAdmin', type: 'address' }],
    name: 'transferAdmin',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'newAdmin', type: 'address' }],
    name: 'transferAdminQuickly',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'uint256', name: 'amount', type: 'uint256' },
      { internalType: 'address payable', name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawEther',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'uint256', name: 'amount', type: 'uint256' },
      { internalType: 'address', name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawToken',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
];
```

#### `KyberHintHandler`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#kyberhinthandler) <a href="#kyberhinthandler" id="kyberhinthandler"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/KyberHintHandler.sol)

```
[
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    name: 'buildEthToTokenHint',
    outputs: [{ internalType: 'bytes', name: 'hint', type: 'bytes' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
    ],
    name: 'buildTokenToEthHint',
    outputs: [{ internalType: 'bytes', name: 'hint', type: 'bytes' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    name: 'buildTokenToTokenHint',
    outputs: [{ internalType: 'bytes', name: 'hint', type: 'bytes' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'parseEthToTokenHint',
    outputs: [
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'ethToTokenAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'parseTokenToEthHint',
    outputs: [
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'tokenToEthAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'tokenSrc', type: 'address' },
      { internalType: 'contract IERC20', name: 'tokenDest', type: 'address' },
      { internalType: 'bytes', name: 'hint', type: 'bytes' },
    ],
    name: 'parseTokenToTokenHint',
    outputs: [
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'tokenToEthType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'tokenToEthReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'tokenToEthAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'tokenToEthSplits',
        type: 'uint256[]',
      },
      {
        internalType: 'enum IKyberHint.TradeType',
        name: 'ethToTokenType',
        type: 'uint8',
      },
      {
        internalType: 'bytes32[]',
        name: 'ethToTokenReserveIds',
        type: 'bytes32[]',
      },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'ethToTokenAddresses',
        type: 'address[]',
      },
      {
        internalType: 'uint256[]',
        name: 'ethToTokenSplits',
        type: 'uint256[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
];
```

#### `KyberStorage`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#kyberstorage) <a href="#kyberstorage" id="kyberstorage"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/KyberStorage.sol)

```
[
  {
    inputs: [
      { internalType: 'address', name: '_admin', type: 'address' },
      {
        internalType: 'contract IKyberHistory',
        name: '_kyberNetworkHistory',
        type: 'address',
      },
      {
        internalType: 'contract IKyberHistory',
        name: '_kyberFeeHandlerHistory',
        type: 'address',
      },
      {
        internalType: 'contract IKyberHistory',
        name: '_kyberDaoHistory',
        type: 'address',
      },
      {
        internalType: 'contract IKyberHistory',
        name: '_kyberMatchingEngineHistory',
        type: 'address',
      },
    ],
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'reserve',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'bytes32',
        name: 'reserveId',
        type: 'bytes32',
      },
      {
        indexed: false,
        internalType: 'enum IKyberStorage.ReserveType',
        name: 'reserveType',
        type: 'uint8',
      },
      {
        indexed: true,
        internalType: 'address',
        name: 'rebateWallet',
        type: 'address',
      },
    ],
    name: 'AddReserveToStorage',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'newAdmin',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'previousAdmin',
        type: 'address',
      },
    ],
    name: 'AdminClaimed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'newAlerter',
        type: 'address',
      },
      { indexed: false, internalType: 'bool', name: 'isAdd', type: 'bool' },
    ],
    name: 'AlerterAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'contract IKyberNetwork',
        name: 'newKyberNetwork',
        type: 'address',
      },
    ],
    name: 'KyberNetworkUpdated',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'bytes32',
        name: 'reserveId',
        type: 'bytes32',
      },
      {
        indexed: false,
        internalType: 'address',
        name: 'reserve',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'src',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'dest',
        type: 'address',
      },
      { indexed: false, internalType: 'bool', name: 'add', type: 'bool' },
    ],
    name: 'ListReservePairs',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'newOperator',
        type: 'address',
      },
      { indexed: false, internalType: 'bool', name: 'isAdd', type: 'bool' },
    ],
    name: 'OperatorAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'reserve',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'bytes32',
        name: 'reserveId',
        type: 'bytes32',
      },
    ],
    name: 'RemoveReserveFromStorage',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'bytes32',
        name: 'reserveId',
        type: 'bytes32',
      },
      {
        indexed: true,
        internalType: 'address',
        name: 'rebateWallet',
        type: 'address',
      },
    ],
    name: 'ReserveRebateWalletSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'pendingAdmin',
        type: 'address',
      },
    ],
    name: 'TransferAdminPending',
    type: 'event',
  },
  {
    inputs: [{ internalType: 'address', name: 'newAlerter', type: 'address' }],
    name: 'addAlerter',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: 'kyberProxy', type: 'address' },
      { internalType: 'uint256', name: 'maxApprovedProxies', type: 'uint256' },
    ],
    name: 'addKyberProxy',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'newOperator', type: 'address' }],
    name: 'addOperator',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: 'reserve', type: 'address' },
      { internalType: 'bytes32', name: 'reserveId', type: 'bytes32' },
      {
        internalType: 'enum IKyberStorage.ReserveType',
        name: 'resType',
        type: 'uint8',
      },
      {
        internalType: 'address payable',
        name: 'rebateWallet',
        type: 'address',
      },
    ],
    name: 'addReserve',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'admin',
    outputs: [{ internalType: 'address', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'claimAdmin',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getAlerters',
    outputs: [{ internalType: 'address[]', name: '', type: 'address[]' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getContracts',
    outputs: [
      {
        internalType: 'address[]',
        name: 'kyberDaoAddresses',
        type: 'address[]',
      },
      {
        internalType: 'address[]',
        name: 'kyberFeeHandlerAddresses',
        type: 'address[]',
      },
      {
        internalType: 'address[]',
        name: 'kyberMatchingEngineAddresses',
        type: 'address[]',
      },
      {
        internalType: 'address[]',
        name: 'kyberNetworkAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getEntitledRebateData',
    outputs: [
      { internalType: 'bool[]', name: 'entitledRebateArr', type: 'bool[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getFeeAccountedData',
    outputs: [
      { internalType: 'bool[]', name: 'feeAccountedArr', type: 'bool[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getKyberProxies',
    outputs: [
      {
        internalType: 'contract IKyberNetworkProxy[]',
        name: '',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'bytes32', name: 'reserveId', type: 'bytes32' }],
    name: 'getListedTokensByReserveId',
    outputs: [
      {
        internalType: 'contract IERC20[]',
        name: 'srcTokens',
        type: 'address[]',
      },
      {
        internalType: 'contract IERC20[]',
        name: 'destTokens',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getOperators',
    outputs: [{ internalType: 'address[]', name: '', type: 'address[]' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getRebateWalletsFromIds',
    outputs: [
      { internalType: 'address[]', name: 'rebateWallets', type: 'address[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'bytes32', name: 'reserveId', type: 'bytes32' }],
    name: 'getReserveAddressesByReserveId',
    outputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    name: 'getReserveAddressesFromIds',
    outputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'uint256', name: 'startIndex', type: 'uint256' },
      { internalType: 'uint256', name: 'endIndex', type: 'uint256' },
    ],
    name: 'getReserveAddressesPerTokenSrc',
    outputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'reserve', type: 'address' }],
    name: 'getReserveDetailsByAddress',
    outputs: [
      { internalType: 'bytes32', name: 'reserveId', type: 'bytes32' },
      { internalType: 'address', name: 'rebateWallet', type: 'address' },
      {
        internalType: 'enum IKyberStorage.ReserveType',
        name: 'resType',
        type: 'uint8',
      },
      { internalType: 'bool', name: 'isFeeAccountedFlag', type: 'bool' },
      { internalType: 'bool', name: 'isEntitledRebateFlag', type: 'bool' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'bytes32', name: 'reserveId', type: 'bytes32' }],
    name: 'getReserveDetailsById',
    outputs: [
      { internalType: 'address', name: 'reserveAddress', type: 'address' },
      { internalType: 'address', name: 'rebateWallet', type: 'address' },
      {
        internalType: 'enum IKyberStorage.ReserveType',
        name: 'resType',
        type: 'uint8',
      },
      { internalType: 'bool', name: 'isFeeAccountedFlag', type: 'bool' },
      { internalType: 'bool', name: 'isEntitledRebateFlag', type: 'bool' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'reserve', type: 'address' }],
    name: 'getReserveId',
    outputs: [{ internalType: 'bytes32', name: '', type: 'bytes32' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'address[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    name: 'getReserveIdsFromAddresses',
    outputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
    ],
    name: 'getReserveIdsPerTokenDest',
    outputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
    ],
    name: 'getReserveIdsPerTokenSrc',
    outputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getReserves',
    outputs: [
      { internalType: 'contract IKyberReserve[]', name: '', type: 'address[]' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32[]', name: 'reserveIds', type: 'bytes32[]' },
      { internalType: 'contract IERC20', name: 'src', type: 'address' },
      { internalType: 'contract IERC20', name: 'dest', type: 'address' },
    ],
    name: 'getReservesData',
    outputs: [
      { internalType: 'bool', name: 'areAllReservesListed', type: 'bool' },
      { internalType: 'bool[]', name: 'feeAccountedArr', type: 'bool[]' },
      { internalType: 'bool[]', name: 'entitledRebateArr', type: 'bool[]' },
      {
        internalType: 'contract IKyberReserve[]',
        name: 'reserveAddresses',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'enum IKyberStorage.ReserveType',
        name: 'resType',
        type: 'uint8',
      },
    ],
    name: 'getReservesPerType',
    outputs: [{ internalType: 'bytes32[]', name: '', type: 'bytes32[]' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'isKyberProxyAdded',
    outputs: [{ internalType: 'bool', name: '', type: 'bool' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberDaoHistory',
    outputs: [
      { internalType: 'contract IKyberHistory', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberFeeHandlerHistory',
    outputs: [
      { internalType: 'contract IKyberHistory', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberMatchingEngineHistory',
    outputs: [
      { internalType: 'contract IKyberHistory', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberNetwork',
    outputs: [
      { internalType: 'contract IKyberNetwork', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberNetworkHistory',
    outputs: [
      { internalType: 'contract IKyberHistory', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32', name: 'reserveId', type: 'bytes32' },
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'bool', name: 'ethToToken', type: 'bool' },
      { internalType: 'bool', name: 'tokenToEth', type: 'bool' },
      { internalType: 'bool', name: 'add', type: 'bool' },
    ],
    name: 'listPairForReserve',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'pendingAdmin',
    outputs: [{ internalType: 'address', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'alerter', type: 'address' }],
    name: 'removeAlerter',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'kyberProxy', type: 'address' }],
    name: 'removeKyberProxy',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'operator', type: 'address' }],
    name: 'removeOperator',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32', name: 'reserveId', type: 'bytes32' },
      { internalType: 'uint256', name: 'startIndex', type: 'uint256' },
    ],
    name: 'removeReserve',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: '_kyberFeeHandler', type: 'address' },
      {
        internalType: 'address',
        name: '_kyberMatchingEngine',
        type: 'address',
      },
    ],
    name: 'setContracts',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bool', name: 'fpr', type: 'bool' },
      { internalType: 'bool', name: 'apr', type: 'bool' },
      { internalType: 'bool', name: 'bridge', type: 'bool' },
      { internalType: 'bool', name: 'utility', type: 'bool' },
      { internalType: 'bool', name: 'custom', type: 'bool' },
      { internalType: 'bool', name: 'orderbook', type: 'bool' },
    ],
    name: 'setEntitledRebatePerReserveType',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bool', name: 'fpr', type: 'bool' },
      { internalType: 'bool', name: 'apr', type: 'bool' },
      { internalType: 'bool', name: 'bridge', type: 'bool' },
      { internalType: 'bool', name: 'utility', type: 'bool' },
      { internalType: 'bool', name: 'custom', type: 'bool' },
      { internalType: 'bool', name: 'orderbook', type: 'bool' },
    ],
    name: 'setFeeAccountedPerReserveType',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: '_kyberDao', type: 'address' }],
    name: 'setKyberDaoContract',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'contract IKyberNetwork',
        name: '_kyberNetwork',
        type: 'address',
      },
    ],
    name: 'setNetworkContract',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'bytes32', name: 'reserveId', type: 'bytes32' },
      { internalType: 'address', name: 'rebateWallet', type: 'address' },
    ],
    name: 'setRebateWallet',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'newAdmin', type: 'address' }],
    name: 'transferAdmin',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: 'newAdmin', type: 'address' }],
    name: 'transferAdminQuickly',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
];
```

#### `KyberFeeHandler (ETH)`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#kyberfeehandler-eth) <a href="#kyberfeehandler-eth" id="kyberfeehandler-eth"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol6/Dao/KyberFeeHandler.sol)

```
[
  {
    inputs: [
      { internalType: 'address', name: '_daoSetter', type: 'address' },
      {
        internalType: 'contract IKyberProxy',
        name: '_kyberProxy',
        type: 'address',
      },
      { internalType: 'address', name: '_kyberNetwork', type: 'address' },
      { internalType: 'contract IERC20', name: '_knc', type: 'address' },
      { internalType: 'uint256', name: '_burnBlockInterval', type: 'uint256' },
      { internalType: 'address', name: '_daoOperator', type: 'address' },
    ],
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'uint256',
        name: 'rewardBps',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'rebateBps',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'burnBps',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'expiryTimestamp',
        type: 'uint256',
      },
      {
        indexed: true,
        internalType: 'uint256',
        name: 'epoch',
        type: 'uint256',
      },
    ],
    name: 'BRRUpdated',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'contract ISanityRate',
        name: 'sanityRate',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'weiToBurn',
        type: 'uint256',
      },
    ],
    name: 'BurnConfigSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'EthReceived',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'address',
        name: 'platformWallet',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'platformFeeWei',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'rewardWei',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'rebateWei',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'address[]',
        name: 'rebateWallets',
        type: 'address[]',
      },
      {
        indexed: false,
        internalType: 'uint256[]',
        name: 'rebatePercentBpsPerWallet',
        type: 'uint256[]',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'burnAmtWei',
        type: 'uint256',
      },
    ],
    name: 'FeeDistributed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'uint256',
        name: 'kncTWei',
        type: 'uint256',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'KncBurned',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'contract IKyberDao',
        name: 'kyberDao',
        type: 'address',
      },
    ],
    name: 'KyberDaoAddressSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'address',
        name: 'kyberNetwork',
        type: 'address',
      },
    ],
    name: 'KyberNetworkUpdated',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: false,
        internalType: 'contract IKyberProxy',
        name: 'kyberProxy',
        type: 'address',
      },
    ],
    name: 'KyberProxyUpdated',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'platformWallet',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'PlatformFeePaid',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'rebateWallet',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'RebatePaid',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'address',
        name: 'staker',
        type: 'address',
      },
      {
        indexed: true,
        internalType: 'uint256',
        name: 'epoch',
        type: 'uint256',
      },
      {
        indexed: true,
        internalType: 'contract IERC20',
        name: 'token',
        type: 'address',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'RewardPaid',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      {
        indexed: true,
        internalType: 'uint256',
        name: 'epoch',
        type: 'uint256',
      },
      {
        indexed: false,
        internalType: 'uint256',
        name: 'rewardsWei',
        type: 'uint256',
      },
    ],
    name: 'RewardsRemovedToBurn',
    type: 'event',
  },
  {
    inputs: [],
    name: 'brrAndEpochData',
    outputs: [
      { internalType: 'uint64', name: 'expiryTimestamp', type: 'uint64' },
      { internalType: 'uint32', name: 'epoch', type: 'uint32' },
      { internalType: 'uint16', name: 'rewardBps', type: 'uint16' },
      { internalType: 'uint16', name: 'rebateBps', type: 'uint16' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'burnBlockInterval',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'burnKnc',
    outputs: [
      { internalType: 'uint256', name: 'kncBurnAmount', type: 'uint256' },
    ],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: 'platformWallet', type: 'address' },
    ],
    name: 'claimPlatformFee',
    outputs: [{ internalType: 'uint256', name: 'amountWei', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: 'rebateWallet', type: 'address' },
    ],
    name: 'claimReserveRebate',
    outputs: [{ internalType: 'uint256', name: 'amountWei', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: 'staker', type: 'address' },
      { internalType: 'uint256', name: 'epoch', type: 'uint256' },
    ],
    name: 'claimStakerReward',
    outputs: [{ internalType: 'uint256', name: 'amountWei', type: 'uint256' }],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'daoOperator',
    outputs: [{ internalType: 'address', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'daoSetter',
    outputs: [{ internalType: 'address', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: '', type: 'address' }],
    name: 'feePerPlatformWallet',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getBRR',
    outputs: [
      { internalType: 'uint256', name: 'rewardBps', type: 'uint256' },
      { internalType: 'uint256', name: 'rebateBps', type: 'uint256' },
      { internalType: 'uint256', name: 'epoch', type: 'uint256' },
    ],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getLatestSanityRate',
    outputs: [
      { internalType: 'uint256', name: 'kncToEthSanityRate', type: 'uint256' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'getSanityRateContracts',
    outputs: [
      {
        internalType: 'contract ISanityRate[]',
        name: 'sanityRates',
        type: 'address[]',
      },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'contract IERC20', name: 'token', type: 'address' },
      { internalType: 'address[]', name: 'rebateWallets', type: 'address[]' },
      {
        internalType: 'uint256[]',
        name: 'rebateBpsPerWallet',
        type: 'uint256[]',
      },
      { internalType: 'address', name: 'platformWallet', type: 'address' },
      { internalType: 'uint256', name: 'platformFee', type: 'uint256' },
      { internalType: 'uint256', name: 'networkFee', type: 'uint256' },
    ],
    name: 'handleFees',
    outputs: [],
    stateMutability: 'payable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: '', type: 'address' },
      { internalType: 'uint256', name: '', type: 'uint256' },
    ],
    name: 'hasClaimedReward',
    outputs: [{ internalType: 'bool', name: '', type: 'bool' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'knc',
    outputs: [{ internalType: 'contract IERC20', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberDao',
    outputs: [
      { internalType: 'contract IKyberDao', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberNetwork',
    outputs: [{ internalType: 'address', name: '', type: 'address' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'kyberProxy',
    outputs: [
      { internalType: 'contract IKyberProxy', name: '', type: 'address' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'lastBurnBlock',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'uint256', name: 'epoch', type: 'uint256' }],
    name: 'makeEpochRewardBurnable',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'readBRRData',
    outputs: [
      { internalType: 'uint256', name: 'rewardBps', type: 'uint256' },
      { internalType: 'uint256', name: 'rebateBps', type: 'uint256' },
      { internalType: 'uint256', name: 'expiryTimestamp', type: 'uint256' },
      { internalType: 'uint256', name: 'epoch', type: 'uint256' },
    ],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'address', name: '', type: 'address' }],
    name: 'rebatePerWallet',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    name: 'rewardsPaidPerEpoch',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    name: 'rewardsPerEpoch',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'contract ISanityRate',
        name: '_sanityRate',
        type: 'address',
      },
      { internalType: 'uint256', name: '_weiToBurn', type: 'uint256' },
    ],
    name: 'setBurnConfigParams',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'contract IKyberDao',
        name: '_kyberDao',
        type: 'address',
      },
    ],
    name: 'setDaoContract',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      {
        internalType: 'contract IKyberProxy',
        name: '_newProxy',
        type: 'address',
      },
    ],
    name: 'setKyberProxy',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [
      { internalType: 'address', name: '_kyberNetwork', type: 'address' },
    ],
    name: 'setNetworkContract',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    inputs: [],
    name: 'totalPayoutBalance',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [],
    name: 'weiToBurn',
    outputs: [{ internalType: 'uint256', name: '', type: 'uint256' }],
    stateMutability: 'view',
    type: 'function',
  },
  { stateMutability: 'payable', type: 'receive' },
];
```

#### `KyberReserve`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#kyberreserve) <a href="#kyberreserve" id="kyberreserve"></a>

[Etherscan link to ABI](https://etherscan.io/address/0xa107dfa919c3f084a7893a260b99586981beb528#code)

```
[
  {
    constant: false,
    inputs: [],
    name: 'enableTrade',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'alerter', type: 'address' }],
    name: 'removeAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'wallet', type: 'address' },
    ],
    name: 'setTokenWallet',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'pendingAdmin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getOperators',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawToken',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAlerter', type: 'address' }],
    name: 'addAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'sanityRatesContract',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'addr', type: 'address' },
      { name: 'approve', type: 'bool' },
    ],
    name: 'approveWithdrawAddress',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'amount', type: 'uint256' },
      { name: 'destination', type: 'address' },
    ],
    name: 'withdraw',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [],
    name: 'disableTrade',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'srcToken', type: 'address' },
      { name: 'srcAmount', type: 'uint256' },
      { name: 'destToken', type: 'address' },
      { name: 'destAddress', type: 'address' },
      { name: 'conversionRate', type: 'uint256' },
      { name: 'validate', type: 'bool' },
    ],
    name: 'trade',
    outputs: [{ name: '', type: 'bool' }],
    payable: true,
    stateMutability: 'payable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [],
    name: 'claimAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdminQuickly',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getAlerters',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'dest', type: 'address' },
      { name: 'srcQty', type: 'uint256' },
      { name: 'blockNumber', type: 'uint256' },
    ],
    name: 'getConversionRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newOperator', type: 'address' }],
    name: 'addOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'dest', type: 'address' },
      { name: 'dstQty', type: 'uint256' },
      { name: 'rate', type: 'uint256' },
    ],
    name: 'getSrcQty',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: '', type: 'address' }],
    name: 'tokenWallet',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'operator', type: 'address' }],
    name: 'removeOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: '_kyberNetwork', type: 'address' },
      { name: '_conversionRates', type: 'address' },
      { name: '_sanityRates', type: 'address' },
    ],
    name: 'setContracts',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'kyberNetwork',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawEther',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'conversionRatesContract',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'tradeEnabled',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: '', type: 'bytes32' }],
    name: 'approvedWithdrawAddresses',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'admin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'getBalance',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'dest', type: 'address' },
      { name: 'srcQty', type: 'uint256' },
      { name: 'rate', type: 'uint256' },
    ],
    name: 'getDestQty',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { name: '_kyberNetwork', type: 'address' },
      { name: '_ratesContract', type: 'address' },
      { name: '_admin', type: 'address' },
    ],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  { payable: true, stateMutability: 'payable', type: 'fallback' },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'amount', type: 'uint256' },
    ],
    name: 'DepositToken',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: true, name: 'origin', type: 'address' },
      { indexed: false, name: 'src', type: 'address' },
      { indexed: false, name: 'srcAmount', type: 'uint256' },
      { indexed: false, name: 'destToken', type: 'address' },
      { indexed: false, name: 'destAmount', type: 'uint256' },
      { indexed: false, name: 'destAddress', type: 'address' },
    ],
    name: 'TradeExecute',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'enable', type: 'bool' }],
    name: 'TradeEnabled',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'addr', type: 'address' },
      { indexed: false, name: 'approve', type: 'bool' },
    ],
    name: 'WithdrawAddressApproved',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'wallet', type: 'address' },
    ],
    name: 'NewTokenWallet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'destination', type: 'address' },
    ],
    name: 'WithdrawFunds',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'network', type: 'address' },
      { indexed: false, name: 'rate', type: 'address' },
      { indexed: false, name: 'sanity', type: 'address' },
    ],
    name: 'SetContractAddresses',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'TokenWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'EtherWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'pendingAdmin', type: 'address' }],
    name: 'TransferAdminPending',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAdmin', type: 'address' },
      { indexed: false, name: 'previousAdmin', type: 'address' },
    ],
    name: 'AdminClaimed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAlerter', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'AlerterAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newOperator', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'OperatorAdded',
    type: 'event',
  },
];
```

#### `ConversionRates`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#conversionrates) <a href="#conversionrates" id="conversionrates"></a>

[Etherscan link to ABI](https://etherscan.io/address/0x798AbDA6Cc246D0EDbA912092A2a3dBd3d11191B#code)

```
[
  {
    constant: false,
    inputs: [{ name: 'alerter', type: 'address' }],
    name: 'removeAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'reserve', type: 'address' }],
    name: 'setReserveAddress',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'disableTokenTrade',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'validRateDurationInBlocks',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'tokens', type: 'address[]' },
      { name: 'baseBuy', type: 'uint256[]' },
      { name: 'baseSell', type: 'uint256[]' },
      { name: 'buy', type: 'bytes14[]' },
      { name: 'sell', type: 'bytes14[]' },
      { name: 'blockNumber', type: 'uint256' },
      { name: 'indices', type: 'uint256[]' },
    ],
    name: 'setBaseRate',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'enableTokenTrade',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'pendingAdmin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getOperators',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getListedTokens',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawToken',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAlerter', type: 'address' }],
    name: 'addAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'numTokensInCurrentCompactData',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'command', type: 'uint256' },
      { name: 'param', type: 'uint256' },
    ],
    name: 'getStepFunctionData',
    outputs: [{ name: '', type: 'int256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'buy', type: 'bytes14[]' },
      { name: 'sell', type: 'bytes14[]' },
      { name: 'blockNumber', type: 'uint256' },
      { name: 'indices', type: 'uint256[]' },
    ],
    name: 'setCompactData',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'duration', type: 'uint256' }],
    name: 'setValidRateDurationInBlocks',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'getTokenBasicData',
    outputs: [
      { name: '', type: 'bool' },
      { name: '', type: 'bool' },
    ],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [],
    name: 'claimAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdminQuickly',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getAlerters',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'getRateUpdateBlock',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'xBuy', type: 'int256[]' },
      { name: 'yBuy', type: 'int256[]' },
      { name: 'xSell', type: 'int256[]' },
      { name: 'ySell', type: 'int256[]' },
    ],
    name: 'setQtyStepFunction',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newOperator', type: 'address' }],
    name: 'addOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'reserveContract',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: '', type: 'address' },
      { name: '', type: 'uint256' },
    ],
    name: 'tokenImbalanceData',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'operator', type: 'address' }],
    name: 'removeOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'currentBlockNumber', type: 'uint256' },
      { name: 'buy', type: 'bool' },
      { name: 'qty', type: 'uint256' },
    ],
    name: 'getRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'xBuy', type: 'int256[]' },
      { name: 'yBuy', type: 'int256[]' },
      { name: 'xSell', type: 'int256[]' },
      { name: 'ySell', type: 'int256[]' },
    ],
    name: 'setImbalanceStepFunction',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'minimalRecordResolution', type: 'uint256' },
      { name: 'maxPerBlockImbalance', type: 'uint256' },
      { name: 'maxTotalImbalance', type: 'uint256' },
    ],
    name: 'setTokenControlInfo',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'buyAmount', type: 'int256' },
      { name: 'rateUpdateBlock', type: 'uint256' },
      { name: 'currentBlock', type: 'uint256' },
    ],
    name: 'recordImbalance',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawEther',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'buy', type: 'bool' },
    ],
    name: 'getBasicRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'addToken',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'getCompactData',
    outputs: [
      { name: '', type: 'uint256' },
      { name: '', type: 'uint256' },
      { name: '', type: 'bytes1' },
      { name: '', type: 'bytes1' },
    ],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'token', type: 'address' }],
    name: 'getTokenControlInfo',
    outputs: [
      { name: '', type: 'uint256' },
      { name: '', type: 'uint256' },
      { name: '', type: 'uint256' },
    ],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'admin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ name: '_admin', type: 'address' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'TokenWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'EtherWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'pendingAdmin', type: 'address' }],
    name: 'TransferAdminPending',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAdmin', type: 'address' },
      { indexed: false, name: 'previousAdmin', type: 'address' },
    ],
    name: 'AdminClaimed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAlerter', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'AlerterAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newOperator', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'OperatorAdded',
    type: 'event',
  },
];
```

#### `LiquidityConversionRates`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#liquidityconversionrates) <a href="#liquidityconversionrates" id="liquidityconversionrates"></a>

[Etherscan link to ABI](https://etherscan.io/address/0x97d7126b6ff7c4d95601912f4cdf790a3cd1edab#code)

```
[
  {
    constant: false,
    inputs: [{ name: 'alerter', type: 'address' }],
    name: 'removeAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'maxSellRateInPrecision',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'reserve', type: 'address' }],
    name: 'setReserveAddress',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'val', type: 'int256' }],
    name: 'abs',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'qtyInwei', type: 'uint256' }],
    name: 'fromWeiToFp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'r', type: 'uint256' },
      { name: 'pMIn', type: 'uint256' },
      { name: 'e', type: 'uint256' },
      { name: 'precision', type: 'uint256' },
    ],
    name: 'pE',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'pendingAdmin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'p', type: 'uint256' },
      { name: 'q', type: 'uint256' },
      { name: 'numPrecisionBits', type: 'uint256' },
    ],
    name: 'ln',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'maxEthCapSellInFp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getOperators',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'BIG_NUMBER',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawToken',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'collectedFeesInTwei',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAlerter', type: 'address' }],
    name: 'addAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'rInFp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'maxEthCapBuyInFp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'formulaPrecision',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: '_rInFp', type: 'uint256' },
      { name: '_pMinInFp', type: 'uint256' },
      { name: '_numFpBits', type: 'uint256' },
      { name: '_maxCapBuyInWei', type: 'uint256' },
      { name: '_maxCapSellInWei', type: 'uint256' },
      { name: '_feeInBps', type: 'uint256' },
      { name: '_maxTokenToEthRateInPrecision', type: 'uint256' },
      { name: '_minTokenToEthRateInPrecision', type: 'uint256' },
    ],
    name: 'setLiquidityParams',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'x', type: 'uint256' },
      { name: 'y', type: 'uint256' },
    ],
    name: 'checkMultOverflow',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'eInFp', type: 'uint256' },
      { name: 'deltaEInFp', type: 'uint256' },
    ],
    name: 'buyRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'eInFp', type: 'uint256' }],
    name: 'sellRateZeroQuantity',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'val', type: 'uint256' }],
    name: 'valueAfterReducingFee',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'numFpBits',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [],
    name: 'claimAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdminQuickly',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getAlerters',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'r', type: 'uint256' },
      { name: 'pMIn', type: 'uint256' },
      { name: 'e', type: 'uint256' },
      { name: 'deltaE', type: 'uint256' },
      { name: 'precision', type: 'uint256' },
    ],
    name: 'deltaTFunc',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'x', type: 'uint256' },
      { name: 'numPrecisionBits', type: 'uint256' },
    ],
    name: 'log2ForSmallNumber',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'p', type: 'uint256' },
      { name: 'q', type: 'uint256' },
      { name: 'precision', type: 'uint256' },
    ],
    name: 'compactFraction',
    outputs: [
      { name: '', type: 'uint256' },
      { name: '', type: 'uint256' },
    ],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'conversionToken', type: 'address' },
      { name: 'buy', type: 'bool' },
      { name: 'qtyInSrcWei', type: 'uint256' },
      { name: 'eInFp', type: 'uint256' },
    ],
    name: 'getRateWithE',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'p', type: 'uint256' },
      { name: 'q', type: 'uint256' },
    ],
    name: 'countLeadingZeros',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'eInFp', type: 'uint256' },
      { name: 'sellInputTokenQtyInFp', type: 'uint256' },
      { name: 'deltaTInFp', type: 'uint256' },
    ],
    name: 'sellRate',
    outputs: [
      { name: 'rateInPrecision', type: 'uint256' },
      { name: 'deltaEInFp', type: 'uint256' },
    ],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'qtyInTwei', type: 'uint256' }],
    name: 'fromTweiToFp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newOperator', type: 'address' }],
    name: 'addOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'r', type: 'uint256' },
      { name: 'pMIn', type: 'uint256' },
      { name: 'e', type: 'uint256' },
      { name: 'deltaT', type: 'uint256' },
      { name: 'precision', type: 'uint256' },
      { name: 'numPrecisionBits', type: 'uint256' },
    ],
    name: 'deltaEFunc',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'feeInBps',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'p', type: 'uint256' },
      { name: 'q', type: 'uint256' },
      { name: 'numPrecisionBits', type: 'uint256' },
    ],
    name: 'logBase2',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'rateInPrecision', type: 'uint256' },
      { name: 'buy', type: 'bool' },
    ],
    name: 'rateAfterValidation',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'reserveContract',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'val', type: 'uint256' }],
    name: 'calcCollectedFee',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'operator', type: 'address' }],
    name: 'removeOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'p', type: 'uint256' },
      { name: 'q', type: 'uint256' },
      { name: 'precision', type: 'uint256' },
    ],
    name: 'exp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'pure',
    type: 'function',
  },
  {
    constant: false,
    inputs: [],
    name: 'resetCollectedFees',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'conversionToken', type: 'address' },
      { name: 'currentBlockNumber', type: 'uint256' },
      { name: 'buy', type: 'bool' },
      { name: 'qtyInSrcWei', type: 'uint256' },
    ],
    name: 'getRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'conversionToken', type: 'address' },
      { name: 'buyAmountInTwei', type: 'int256' },
      { name: 'rateUpdateBlock', type: 'uint256' },
      { name: 'currentBlock', type: 'uint256' },
    ],
    name: 'recordImbalance',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawEther',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'eInFp', type: 'uint256' }],
    name: 'buyRateZeroQuantity',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'maxBuyRateInPrecision',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'minSellRateInPrecision',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'pMinInFp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'maxQtyInFp',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'admin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'minBuyRateInPrecision',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'token',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [
      { name: '_admin', type: 'address' },
      { name: '_token', type: 'address' },
    ],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'reserve', type: 'address' }],
    name: 'ReserveAddressSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'rInFp', type: 'uint256' },
      { indexed: false, name: 'pMinInFp', type: 'uint256' },
      { indexed: false, name: 'numFpBits', type: 'uint256' },
      { indexed: false, name: 'maxCapBuyInFp', type: 'uint256' },
      { indexed: false, name: 'maxEthCapSellInFp', type: 'uint256' },
      { indexed: false, name: 'feeInBps', type: 'uint256' },
      { indexed: false, name: 'formulaPrecision', type: 'uint256' },
      { indexed: false, name: 'maxQtyInFp', type: 'uint256' },
      { indexed: false, name: 'maxBuyRateInPrecision', type: 'uint256' },
      { indexed: false, name: 'minBuyRateInPrecision', type: 'uint256' },
      { indexed: false, name: 'maxSellRateInPrecision', type: 'uint256' },
      { indexed: false, name: 'minSellRateInPrecision', type: 'uint256' },
    ],
    name: 'LiquidityParamsSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'resetFeesInTwei', type: 'uint256' }],
    name: 'CollectedFeesReset',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'TokenWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'EtherWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'pendingAdmin', type: 'address' }],
    name: 'TransferAdminPending',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAdmin', type: 'address' },
      { indexed: false, name: 'previousAdmin', type: 'address' },
    ],
    name: 'AdminClaimed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAlerter', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'AlerterAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newOperator', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'OperatorAdded',
    type: 'event',
  },
];
```

#### `SanityRates`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#sanityrates) <a href="#sanityrates" id="sanityrates"></a>

[Etherscan link to ABI](https://etherscan.io/address/0xdfc85C08d5e5924aB49750E006CF8a826ffb7B13#code)

```
[
  {
    constant: false,
    inputs: [{ name: 'alerter', type: 'address' }],
    name: 'removeAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'pendingAdmin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getOperators',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawToken',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAlerter', type: 'address' }],
    name: 'addAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: '', type: 'address' }],
    name: 'reasonableDiffInBps',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'srcs', type: 'address[]' },
      { name: 'diff', type: 'uint256[]' },
    ],
    name: 'setReasonableDiff',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [],
    name: 'claimAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdminQuickly',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getAlerters',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newOperator', type: 'address' }],
    name: 'addOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'dest', type: 'address' },
    ],
    name: 'getSanityRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'operator', type: 'address' }],
    name: 'removeOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: '', type: 'address' }],
    name: 'tokenRate',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawEther',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'srcs', type: 'address[]' },
      { name: 'rates', type: 'uint256[]' },
    ],
    name: 'setSanityRates',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'admin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ name: '_admin', type: 'address' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'TokenWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'EtherWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'pendingAdmin', type: 'address' }],
    name: 'TransferAdminPending',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAdmin', type: 'address' },
      { indexed: false, name: 'previousAdmin', type: 'address' },
    ],
    name: 'AdminClaimed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAlerter', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'AlerterAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newOperator', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'OperatorAdded',
    type: 'event',
  },
];
```

#### `KyberNetworkProxy (V1)`[​](https://docs.kyberswap.com/Legacy/api-abi/contract-abis/api\_abi-abi#kybernetworkproxy-v1) <a href="#kybernetworkproxy-v1" id="kybernetworkproxy-v1"></a>

[Smart Contract URL](https://github.com/KyberNetwork/smart-contracts/blob/Katalyst/contracts/sol4/KyberProxyV1.sol)

```
[
  {
    constant: false,
    inputs: [{ name: 'alerter', type: 'address' }],
    name: 'removeAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'enabled',
    outputs: [{ name: '', type: 'bool' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'pendingAdmin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getOperators',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'srcAmount', type: 'uint256' },
      { name: 'dest', type: 'address' },
      { name: 'destAddress', type: 'address' },
      { name: 'maxDestAmount', type: 'uint256' },
      { name: 'minConversionRate', type: 'uint256' },
      { name: 'walletId', type: 'address' },
      { name: 'hint', type: 'bytes' },
    ],
    name: 'tradeWithHint',
    outputs: [{ name: '', type: 'uint256' }],
    payable: true,
    stateMutability: 'payable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'srcAmount', type: 'uint256' },
      { name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapTokenToEther',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawToken',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'maxGasPrice',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAlerter', type: 'address' }],
    name: 'addAlerter',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'kyberNetworkContract',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'user', type: 'address' }],
    name: 'getUserCapInWei',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'srcAmount', type: 'uint256' },
      { name: 'dest', type: 'address' },
      { name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapTokenToToken',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [],
    name: 'claimAdmin',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'minConversionRate', type: 'uint256' },
    ],
    name: 'swapEtherToToken',
    outputs: [{ name: '', type: 'uint256' }],
    payable: true,
    stateMutability: 'payable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newAdmin', type: 'address' }],
    name: 'transferAdminQuickly',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'getAlerters',
    outputs: [{ name: '', type: 'address[]' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'dest', type: 'address' },
      { name: 'srcQty', type: 'uint256' },
    ],
    name: 'getExpectedRate',
    outputs: [
      { name: 'expectedRate', type: 'uint256' },
      { name: 'slippageRate', type: 'uint256' },
    ],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'user', type: 'address' },
      { name: 'token', type: 'address' },
    ],
    name: 'getUserCapInTokenWei',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'newOperator', type: 'address' }],
    name: 'addOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: '_kyberNetworkContract', type: 'address' }],
    name: 'setKyberNetworkContract',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [{ name: 'operator', type: 'address' }],
    name: 'removeOperator',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [{ name: 'field', type: 'bytes32' }],
    name: 'info',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'src', type: 'address' },
      { name: 'srcAmount', type: 'uint256' },
      { name: 'dest', type: 'address' },
      { name: 'destAddress', type: 'address' },
      { name: 'maxDestAmount', type: 'uint256' },
      { name: 'minConversionRate', type: 'uint256' },
      { name: 'walletId', type: 'address' },
    ],
    name: 'trade',
    outputs: [{ name: '', type: 'uint256' }],
    payable: true,
    stateMutability: 'payable',
    type: 'function',
  },
  {
    constant: false,
    inputs: [
      { name: 'amount', type: 'uint256' },
      { name: 'sendTo', type: 'address' },
    ],
    name: 'withdrawEther',
    outputs: [],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'function',
  },
  {
    constant: true,
    inputs: [
      { name: 'token', type: 'address' },
      { name: 'user', type: 'address' },
    ],
    name: 'getBalance',
    outputs: [{ name: '', type: 'uint256' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    constant: true,
    inputs: [],
    name: 'admin',
    outputs: [{ name: '', type: 'address' }],
    payable: false,
    stateMutability: 'view',
    type: 'function',
  },
  {
    inputs: [{ name: '_admin', type: 'address' }],
    payable: false,
    stateMutability: 'nonpayable',
    type: 'constructor',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: true, name: 'trader', type: 'address' },
      { indexed: false, name: 'src', type: 'address' },
      { indexed: false, name: 'dest', type: 'address' },
      { indexed: false, name: 'actualSrcAmount', type: 'uint256' },
      { indexed: false, name: 'actualDestAmount', type: 'uint256' },
    ],
    name: 'ExecuteTrade',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newNetworkContract', type: 'address' },
      { indexed: false, name: 'oldNetworkContract', type: 'address' },
    ],
    name: 'KyberNetworkSet',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'token', type: 'address' },
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'TokenWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'amount', type: 'uint256' },
      { indexed: false, name: 'sendTo', type: 'address' },
    ],
    name: 'EtherWithdraw',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [{ indexed: false, name: 'pendingAdmin', type: 'address' }],
    name: 'TransferAdminPending',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAdmin', type: 'address' },
      { indexed: false, name: 'previousAdmin', type: 'address' },
    ],
    name: 'AdminClaimed',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newAlerter', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'AlerterAdded',
    type: 'event',
  },
  {
    anonymous: false,
    inputs: [
      { indexed: false, name: 'newOperator', type: 'address' },
      { indexed: false, name: 'isAdd', type: 'bool' },
    ],
    name: 'OperatorAdded',
    type: 'event',
  },
];
```
