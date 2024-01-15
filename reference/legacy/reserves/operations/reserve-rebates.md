# Reserve Rebates

{% hint style="warning" %}
You are referring to the **`Legacy`** version of KyberSwap docs.

For the most updated information, please refer to:

* [**`Classic`**](../../../../liquidity-solutions/kyberswap-classic/)
* [**`Elastic`**](../../../../liquidity-solutions/kyberswap-elastic/)
* [**`Limit Order`**](../../../../kyberswap-solutions/limit-order/)
* [**`Aggregator`**](../../../../kyberswap-solutions/kyberswap-aggregator/)
{% endhint %}

A network fee may be charged for a Kyber trade (dependent on reserve type). The network fee percentage is determined on the KyberDAO, and may change over time.

The KyberDAO also gets to determine what happens to the network fee. It is split 3 ways:

1. Burning of KNC
2. Staker rewards
3. Reserve Rebates

The motivation for reserve rebates is to reward selected reserves based on their performance (i.e. amount of trade volume they facilitate). This incentivizes reserves to provide better liquidity and tighter spreads, thereby driving greater volume, value, and network fees.

### How do I specify the reserve rebate wallet for these rebates?[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#how-do-i-specify-the-reserve-rebate-wallet-for-these-rebates) <a href="#how-do-i-specify-the-reserve-rebate-wallet-for-these-rebates" id="how-do-i-specify-the-reserve-rebate-wallet-for-these-rebates"></a>

Whenever a reserve is added to the network, the rebate wallet must also be specified as well.

### What if I need to change the rebate wallet address?[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#what-if-i-need-to-change-the-rebate-wallet-address) <a href="#what-if-i-need-to-change-the-rebate-wallet-address" id="what-if-i-need-to-change-the-rebate-wallet-address"></a>

Notify the Kyber team / network maintainers!

### Do the rebates go automatically to the rebate wallet I specified?[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#do-the-rebates-go-automatically-to-the-rebate-wallet-i-specified) <a href="#do-the-rebates-go-automatically-to-the-rebate-wallet-i-specified" id="do-the-rebates-go-automatically-to-the-rebate-wallet-i-specified"></a>

No. You will have to claim them manually through the KyberFeeHandler contract(s).

### How do I view the rebate amount claimable?[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#how-do-i-view-the-rebate-amount-claimable) <a href="#how-do-i-view-the-rebate-amount-claimable" id="how-do-i-view-the-rebate-amount-claimable"></a>

Call the `rebatePerWallet` method of the KyberFeeHandler contract(s). Note that for gas optimizations, 1 ether wei is kept inside the contract, so the claimable amount has to be subtract by 1.

Kindly refer to the example below.

### How do I claim reserve rebates?[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#how-do-i-claim-reserve-rebates) <a href="#how-do-i-claim-reserve-rebates" id="how-do-i-claim-reserve-rebates"></a>

Call the `claimReserveRebate` method of the KyberFeeHandler contract(s).

Kindly refer to the example below.

### Example[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#example) <a href="#example" id="example"></a>

#### Checking Rebates Claimable[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#checking-rebates-claimable) <a href="#checking-rebates-claimable" id="checking-rebates-claimable"></a>

**Etherscan**[**​**](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#etherscan)

1. Navigate to the "Read Contract" tab of the Kyber Fee Handler contract in Etherscan. Example: [https://ropsten.etherscan.io/address/0xe57B2c3b4E44730805358131a6Fc244C57178Da7#readContract](https://ropsten.etherscan.io/address/0xe57B2c3b4E44730805358131a6Fc244C57178Da7#readContract)

![Get Rebates Step 1](https://docs.kyberswap.com/assets/images/getFeesClaimable-1f040de32b9126c954cb1c17c704f309.jpg)

1. Go to the `rebatePerWallet` function, input your rebate wallet address, then click on the "Query" button.

![Get Rebates Step 2](https://docs.kyberswap.com/assets/images/getRebates-1-1dae6d6df3e0739979a793f837688e54.jpg)

1. You should be able to see the amount claimable. This is in ETH wei. Note that you have to subtract this amount by 1 wei. Example: In the image below, the amount claimable is `9288172147833692 - 1` \~= 0.00928 ETH - 1 ether wei.

![Get Rebates Step 3](https://docs.kyberswap.com/assets/images/getRebates-2-1da1967db34e9e1ac5cd9e4a459ac78f.jpg)

**ethers.js**[**​**](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#ethersjs)

1. Change the `REBATE_WALLET_ADDRESS` to be the desired wallet address for which you would like to check the rebates claimable.
2. Change the `FEE_HANDLER_ADDRESS` to the KyberFeeHandler contract address.

```javascript
// DISCLAIMER: Code snippets in this guide are just examples and you
// should always do your own testing. If you have questions, visit our
// https://t.me/KyberDeveloper.

const ethers = require('ethers');
const BN = ethers.BigNumber;
const NETWORK = "ropsten";
const provider = new ethers.getDefaultProvider(NETWORK);

// Replace the addresses below
const REBATE_WALLET_ADDRESS = "REBATE_WALLET_ADDRESS"; // Eg. "0x8640d5a5c11782ea9cc63833843a7b8f8911d568"
const FEE_HANDLER_ADDRESS = "FEE_HANDLER_ADDRESS"; // Eg. "0xe57B2c3b4E44730805358131a6Fc244C57178Da7"

const KyberFeeHandlerABI = [{"inputs":[{"internalType":"address","name":"_daoSetter","type":"address"},{"internalType":"contract IKyberProxy","name":"_kyberProxy","type":"address"},{"internalType":"address","name":"_kyberNetwork","type":"address"},{"internalType":"contract IERC20","name":"_knc","type":"address"},{"internalType":"uint256","name":"_burnBlockInterval","type":"uint256"},{"internalType":"address","name":"_daoOperator","type":"address"}],"stateMutability":"nonpayable","type":"constructor"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"uint256","name":"rewardBps","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"rebateBps","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"burnBps","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"expiryTimestamp","type":"uint256"},{"indexed":true,"internalType":"uint256","name":"epoch","type":"uint256"}],"name":"BRRUpdated","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"contract ISanityRate","name":"sanityRate","type":"address"},{"indexed":false,"internalType":"uint256","name":"weiToBurn","type":"uint256"}],"name":"BurnConfigSet","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"EthReceived","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"contract IERC20","name":"token","type":"address"},{"indexed":true,"internalType":"address","name":"platformWallet","type":"address"},{"indexed":false,"internalType":"uint256","name":"platformFeeWei","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"rewardWei","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"rebateWei","type":"uint256"},{"indexed":false,"internalType":"address[]","name":"rebateWallets","type":"address[]"},{"indexed":false,"internalType":"uint256[]","name":"rebatePercentBpsPerWallet","type":"uint256[]"},{"indexed":false,"internalType":"uint256","name":"burnAmtWei","type":"uint256"}],"name":"FeeDistributed","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"uint256","name":"kncTWei","type":"uint256"},{"indexed":true,"internalType":"contract IERC20","name":"token","type":"address"},{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"KncBurned","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"contract IKyberDao","name":"kyberDao","type":"address"}],"name":"KyberDaoAddressSet","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"kyberNetwork","type":"address"}],"name":"KyberNetworkUpdated","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"contract IKyberProxy","name":"kyberProxy","type":"address"}],"name":"KyberProxyUpdated","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"address","name":"platformWallet","type":"address"},{"indexed":true,"internalType":"contract IERC20","name":"token","type":"address"},{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"PlatformFeePaid","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"address","name":"rebateWallet","type":"address"},{"indexed":true,"internalType":"contract IERC20","name":"token","type":"address"},{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"RebatePaid","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"address","name":"staker","type":"address"},{"indexed":true,"internalType":"uint256","name":"epoch","type":"uint256"},{"indexed":true,"internalType":"contract IERC20","name":"token","type":"address"},{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"RewardPaid","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"epoch","type":"uint256"},{"indexed":false,"internalType":"uint256","name":"rewardsWei","type":"uint256"}],"name":"RewardsRemovedToBurn","type":"event"},{"inputs":[],"name":"brrAndEpochData","outputs":[{"internalType":"uint64","name":"expiryTimestamp","type":"uint64"},{"internalType":"uint32","name":"epoch","type":"uint32"},{"internalType":"uint16","name":"rewardBps","type":"uint16"},{"internalType":"uint16","name":"rebateBps","type":"uint16"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"burnBlockInterval","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"burnKnc","outputs":[{"internalType":"uint256","name":"kncBurnAmount","type":"uint256"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"platformWallet","type":"address"}],"name":"claimPlatformFee","outputs":[{"internalType":"uint256","name":"amountWei","type":"uint256"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"rebateWallet","type":"address"}],"name":"claimReserveRebate","outputs":[{"internalType":"uint256","name":"amountWei","type":"uint256"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"staker","type":"address"},{"internalType":"uint256","name":"epoch","type":"uint256"}],"name":"claimStakerReward","outputs":[{"internalType":"uint256","name":"amountWei","type":"uint256"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"daoOperator","outputs":[{"internalType":"address","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"daoSetter","outputs":[{"internalType":"address","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"","type":"address"}],"name":"feePerPlatformWallet","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"getBRR","outputs":[{"internalType":"uint256","name":"rewardBps","type":"uint256"},{"internalType":"uint256","name":"rebateBps","type":"uint256"},{"internalType":"uint256","name":"epoch","type":"uint256"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"getLatestSanityRate","outputs":[{"internalType":"uint256","name":"kncToEthSanityRate","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"getSanityRateContracts","outputs":[{"internalType":"contract ISanityRate[]","name":"sanityRates","type":"address[]"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"contract IERC20","name":"token","type":"address"},{"internalType":"address[]","name":"rebateWallets","type":"address[]"},{"internalType":"uint256[]","name":"rebateBpsPerWallet","type":"uint256[]"},{"internalType":"address","name":"platformWallet","type":"address"},{"internalType":"uint256","name":"platformFee","type":"uint256"},{"internalType":"uint256","name":"networkFee","type":"uint256"}],"name":"handleFees","outputs":[],"stateMutability":"payable","type":"function"},{"inputs":[{"internalType":"address","name":"","type":"address"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"hasClaimedReward","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"knc","outputs":[{"internalType":"contract IERC20","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"kyberDao","outputs":[{"internalType":"contract IKyberDao","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"kyberNetwork","outputs":[{"internalType":"address","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"kyberProxy","outputs":[{"internalType":"contract IKyberProxy","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"lastBurnBlock","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"epoch","type":"uint256"}],"name":"makeEpochRewardBurnable","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"readBRRData","outputs":[{"internalType":"uint256","name":"rewardBps","type":"uint256"},{"internalType":"uint256","name":"rebateBps","type":"uint256"},{"internalType":"uint256","name":"expiryTimestamp","type":"uint256"},{"internalType":"uint256","name":"epoch","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"","type":"address"}],"name":"rebatePerWallet","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"","type":"uint256"}],"name":"rewardsPaidPerEpoch","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"","type":"uint256"}],"name":"rewardsPerEpoch","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"contract ISanityRate","name":"_sanityRate","type":"address"},{"internalType":"uint256","name":"_weiToBurn","type":"uint256"}],"name":"setBurnConfigParams","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"contract IKyberDao","name":"_kyberDao","type":"address"}],"name":"setDaoContract","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"contract IKyberProxy","name":"_newProxy","type":"address"}],"name":"setKyberProxy","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"_kyberNetwork","type":"address"}],"name":"setNetworkContract","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"totalPayoutBalance","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"weiToBurn","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"stateMutability":"payable","type":"receive"}];

async function main() {
  KyberFeeHandlerContract = new ethers.Contract(
    FEE_HANDLER_ADDRESS,
    KyberFeeHandlerABI,
    provider
  );

  let rebatesClaimable = await KyberFeeHandlerContract.rebatePerWallet(REBATE_WALLET_ADDRESS);
  if rebatesClaimable.gt(BN.from(0)) {
    rebatesClaimable = rebatesClaimable.sub(new BN(1));
  }
}

main();
```

#### Claiming Rebates[​](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#claiming-rebates) <a href="#claiming-rebates" id="claiming-rebates"></a>

**Etherscan**[**​**](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#etherscan-1)

**Note:** This method requires your wallet address to be imported into Metamask. You will have to use other methods (Eg. MyCrypto / MyEtherWallet) otherwise.

1. Navigate to the "Write Contract" tab of the Kyber Fee Handler contract in Etherscan. Example: [https://ropsten.etherscan.io/address/0xe57B2c3b4E44730805358131a6Fc244C57178Da7#writeContract](https://ropsten.etherscan.io/address/0xe57B2c3b4E44730805358131a6Fc244C57178Da7#writeContract)

![Claim Rebates Step 1](https://docs.kyberswap.com/assets/images/claimFees-1-d544cfb417b73928a5ebecc2ce236bae.jpg)

2. Click on the "Connect to Web3" button.

![Claim Rebates Step 2](https://docs.kyberswap.com/assets/images/claimFees-2-7730e66dcd58ed817db00872e75516b0.jpg)

3. Go to the `claimReserveRebate` function, input your rebate wallet address, then click on the "Write" button. Confirm the transaction details in Metamask.

![Claim Rebates Step 3](https://docs.kyberswap.com/assets/images/claimReserveRebate-64d2f1ec7316c04e336c52446c437a62.jpg)

**ethers.js**[**​**](https://docs.kyberswap.com/Legacy/reserves/operation/reserves-rebates#ethersjs-1)

1. Change the `REBATE_WALLET_ADDRESS` to be the desired wallet address for which rebates can be claimed from.
2. Change the `FEE_HANDLER_ADDRESS` to the KyberFeeHandler contract address.
3. Change `SENDER_ADDRESS_PRIVATE_KEY` to the private key of an ETH address to send the transaction. This can be any wallet address (ie. does not necessarily have to be `REBATE_WALLET_ADDRESS`). Kindly ensure that this address **has sufficient funds** to send the transaction.

```javascript
// DISCLAIMER: Code snippets in this guide are just examples and you
// should always do your own testing. If you have questions, visit our
// https://t.me/KyberDeveloper.

const ethers = require('ethers');
const BN = ethers.BigNumber;
const NETWORK = 'ropsten';
const provider = new ethers.getDefaultProvider(NETWORK);

// Replace the addresses below
const REBATE_WALLET_ADDRESS = 'REBATE_WALLET_ADDRESS'; // Eg. "0x8640d5a5c11782ea9cc63833843a7b8f8911d568"
const FEE_HANDLER_ADDRESS = 'FEE_HANDLER_ADDRESS'; // Eg. "0xe57B2c3b4E44730805358131a6Fc244C57178Da7"
const SENDER_ADDRESS_PRIVATE_KEY = 'SENDER_ADDRESS_PRIVATE_KEY';
const signer = new ethers.Wallet(SENDER_ADDRESS_PRIVATE_KEY, provider);

const KyberFeeHandlerABI = [
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

async function main() {
  KyberFeeHandlerContract = new ethers.Contract(
    FEE_HANDLER_ADDRESS,
    KyberFeeHandlerABI,
    signer,
  );

  await KyberFeeHandlerContract.claimReserveRebate(REBATE_WALLET_ADDRESS);
}

main();
```
