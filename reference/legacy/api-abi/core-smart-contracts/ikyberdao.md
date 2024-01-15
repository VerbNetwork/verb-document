# IKyberDao

{% hint style="warning" %}
You are referring to the **`Legacy`** version of KyberSwap docs.

For the most updated information, please refer to:

* [**`Classic`**](../../../../liquidity-solutions/kyberswap-classic/)
* [**`Elastic`**](../../../../liquidity-solutions/kyberswap-elastic/)
* [**`Limit Order`**](../../../../kyberswap-solutions/limit-order/)
* [**`Aggregator`**](../../../../kyberswap-solutions/kyberswap-aggregator/)
{% endhint %}

## interface IKyberDao

is [IEpochUtils](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-iepochutils.md) imports [IEpochUtils](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-iepochutils.md)

_Source_: [IKyberDao.sol](https://github.com/KyberNetwork/smart-contracts/blob/master/contracts/sol6/IKyberDao.sol)



### INDEX[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao#index) <a href="#index" id="index"></a>

\<AUTOGENERATED\_TABLE\_OF\_CONTENTS>

### REFERENCE[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao#reference) <a href="#reference" id="reference"></a>

#### Events[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao#events) <a href="#events" id="events"></a>

#### `Voted`[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao#voted) <a href="#voted" id="voted"></a>

Event logging the voting of a campaign at epoch.



event **Voted**(address staker, uint256 epoch, uint256 campaignID, uint256 option) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | `staker` | address | staker's address | | `epoch` | uint256 | epoch number where campaign was voted | | `campaignID` | uint256 | campaign's ID | | `option` | uint256 | ID of option voted for | Signature: 0xc32b42768a47a585121e9b8d7a2ab9d3f34c326a192dee11ee1732e3d18313f3

\


#### Functions[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao#functions) <a href="#functions" id="functions"></a>

#### `vote`[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao#vote) <a href="#vote" id="vote"></a>

Votes for an option of a campaign, where options are indexed from 1 to N number of options.



function **vote**(uint256 campaignID, uint256 option) external | Parameter | Type | Description | | --------- |:-----:|:-----------:| | `campaignID` | uint256 | ID of campaign | | `option` | uint256 | ID of option |

\
\### \`getLatestNetworkFeeData\` Returns the latest network fee data and expiry timestamp. \_\_\_ function \_\_getLatestNetworkFeeData\_\_() external view returns (uint256 feeInBps, uint256 expiryTimestamp)\ \*\*Returns:\*\*\ feeInBps - network fee in BPS expiryTimestamp - the timestamp when the fee will expire and needs to be updated\
\### \`shouldBurnRewardForEpoch\` Since some epochs have rewards but no one can claim it, return true if those rewards should be burned. \_\_\_ function \_\_shouldBurnRewardForEpoch\_\_(uint256 epoch) external view returns (bool) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`epoch\` | uint256 | epoch number to check | \*\*Returns:\*\*\ \`true\` if rewards should be burned for the epoch, \`false\` otherwise\
\### \`getPastEpochRewardPercentageInPrecision\` Returns the staker's reward percentage in precision for a past epoch only. \_\_\_ function \_\_getPastEpochRewardPercentageInPrecision\_\_(address staker, uint256 epoch) external view returns (uint256) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`staker\` | address | staker's address | | \`epoch\` | uint256 | past epoch number | \*\*Returns:\*\*\ Past epoch reward percentage in precision for the staker\
\### \`getCurrentEpochRewardPercentageInPrecision\` Returns the staker's reward percentage in precision for the current epoch. Reward percentage is not finalized until the current epoch has ended. \_\_\_ function \_\_getCurrentEpochRewardPercentageInPrecision\_\_(address staker) external view returns (uint256) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`staker\` | address | staker's address | \*\*Returns:\*\*\ Current epoch reward percentage in precision for the staker