# SanityRates

{% hint style="warning" %}
You are referring to the **`Legacy`** version of KyberSwap docs.

For the most updated information, please refer to:

* [**`Classic`**](../../../../liquidity-solutions/kyberswap-classic/)
* [**`Elastic`**](../../../../liquidity-solutions/kyberswap-elastic/)
* [**`Limit Order`**](../../../../kyberswap-solutions/limit-order/)
* [**`Aggregator`**](../../../../kyberswap-solutions/kyberswap-aggregator/)
{% endhint %}

## contract SanityRates

is [SanityRatesInterface](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityratesinterface.md), [Withdrawable](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-withdrawable.md), Utils\ imports ERC20Interface, [Withdrawable](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-withdrawable.md), Utils, [SanityRatesInterface](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityratesinterface.md)

_Source_: [SanityRates.sol](https://github.com/KyberNetwork/smart-contracts/blob/master/contracts/SanityRates.sol)

The SanityRates contract's role is provide a safeguard for reserves whereby trades are disabled in the event exchange rates fall below the lower limit or rise above the upper limit of the sanity rates.



### INDEX[​](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityrates#index) <a href="#index" id="index"></a>

\<AUTOGENERATED\_TABLE\_OF\_CONTENTS>

### REFERENCE[​](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityrates#reference) <a href="#reference" id="reference"></a>

#### Functions[​](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityrates#functions) <a href="#functions" id="functions"></a>

#### `SanityRates`[​](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityrates#sanityrates) <a href="#sanityrates" id="sanityrates"></a>

Contract constructor. Note that constructor methods are called exactly once during contract instantiation and cannot be called again.



function **SanityRates**(address \_admin) public | Parameter | Type | Description | | ----------|:-------:|:--------------------:| | `_admin` | address | address of the admin |\


#### `getSanityRate`[​](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityrates#getsanityrate) <a href="#getsanityrate" id="getsanityrate"></a>

Gets the sanity rate for a pair of tokens.



function **getSanityRate**(ERC20 src, ERC20 dest) public view returns (uint) | Parameter | Type | Description | | --------- |:-----:|:----------------------------------------:| | `src` | ERC20 | source ERC20 token contract address | | `dest` | ERC20 | destination ERC20 token contract address | **Returns:**\ The sanity rate for the pair of tokens



Web3 Example:

```
// DISCLAIMER: Code snippets in this guide are just examples and you
// should always do your own testing. If you have questions, visit our
// https://t.me/KyberDeveloper.

let sanityRate = await SanityRates.methods
  .getSanityRate(
    '0xdd974D5C2e2928deA5F71b9825b8b646686BD200', //ERC20 src: KNC token
    '0xeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee', //ERC20 dest: ETH
  )
  .call();
```

\


#### `setReasonableDiff`[​](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityrates#setreasonablediff) <a href="#setreasonablediff" id="setreasonablediff"></a>

Set reasonable conversion rate difference in percentage (any conversion rate outside of this range is considered unreasonable).



function **setReasonableDiff**(ERC20\[] srcs, uint\[] diff) public | Parameter | Type | Description | | --------- |:-----:|:-----------------------------------------------:| | `srcs` | ERC20\[] | list of source ERC20 token contract addresses | | `diff` | uint\[] | list of reasonableDiffs in basis points (bps)\
`1 bps = 0.01%`\
Modifiers: [onlyAdmin](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-permissiongroups.md#onlyadmin) |



Web3 Example:

```
// DISCLAIMER: Code snippets in this guide are just examples and you
// should always do your own testing. If you have questions, visit our
// https://t.me/KyberDeveloper.

SanityRates.methods
  .setReasonableDiff(
    ['0xdd974D5C2e2928deA5F71b9825b8b646686BD200'], //ERC20[] srcs: [KNC token]
    [1000], //uint[] diff: 10% = 1000 bps
  )
  .send(
    {
      from: adminAddress,
    },
    (err, res) => {
      console.log(`Err: ${err}`);
      console.log(`Res: ${res}`);
    },
  );
```

\


#### `setSanityRates`[​](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-sanityrates#setsanityrates) <a href="#setsanityrates" id="setsanityrates"></a>

Sets the sanity rate for a list of tokens.



function setSanityRates(ERC20\[] srcs, uint\[] rates) public | Parameter | Type | Description | | --------- |:-------:|:---------------------------------------------:| | `srcs` | ERC20\[] | list of source ERC20 token contract addresses | | `rates` | uint\[] | list of rates in ETH wei | Modifiers: [onlyOperator](https://docs.kyberswap.com/Legacy/api-abi/misc/api\_abi-permissiongroups.md#onlyoperator)



Web3 Example:

```
// DISCLAIMER: Code snippets in this guide are just examples and you
// should always do your own testing. If you have questions, visit our
// https://t.me/KyberDeveloper.

SanityRates.methods
  .setSanityRates(
    ['0xdd974D5C2e2928deA5F71b9825b8b646686BD200'], //ERC20[] srcs: [KNC token]
    [2000000000000000], //uint[] rates: 1 KNC = 0.002 ETH = 2000000000000000 wei
  )
  .send(
    {
      from: operatorAddress,
    },
    (err, res) => {
      console.log(`Err: ${err}`);
      console.log(`Res: ${res}`);
    },
  );
```