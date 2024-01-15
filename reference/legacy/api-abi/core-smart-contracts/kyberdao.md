# KyberDao

{% hint style="warning" %}
You are referring to the **`Legacy`** version of KyberSwap docs.

For the most updated information, please refer to:

* [**`Classic`**](../../../../liquidity-solutions/kyberswap-classic/)
* [**`Elastic`**](../../../../liquidity-solutions/kyberswap-elastic/)
* [**`Limit Order`**](../../../../kyberswap-solutions/limit-order/)
* [**`Aggregator`**](../../../../kyberswap-solutions/kyberswap-aggregator/)
{% endhint %}

## contract KyberDao

is [IKyberDao](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao.md), [EpochUtils](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-epochutils.md), ReentrancyGuard, Utils5, DaoOperator\ imports [EpochUtils](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-epochutils.md), DaoOperator, [KyberStaking](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberstaking.md), IERC20, [IKyberDao](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-ikyberdao.md), ReentrancyGuard, Utils5

_Source_: [KyberDao.sol](https://github.com/KyberNetwork/smart-contracts/blob/master/contracts/sol6/Dao/KyberDao.sol)



### INDEX[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberdao#index) <a href="#index" id="index"></a>

\<AUTOGENERATED\_TABLE\_OF\_CONTENTS>

### REFERENCE[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberdao#reference) <a href="#reference" id="reference"></a>

#### Events[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberdao#events) <a href="#events" id="events"></a>

#### `NewCampaignCreated`[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberdao#newcampaigncreated) <a href="#newcampaigncreated" id="newcampaigncreated"></a>

Event for logging the creation of a new campaign.



event **NewCampaignCreated**(CampaignType campaignType, uint256 campaignID, uint256 startTimestamp, uint256 endTimestamp, uint256 minPercentageInPrecision, uint256 cInPrecision, uint256 tInPrecision, uint256\[] options, bytes link) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | `campaignType` | CampaignType | type of campaign (General, NetworkFee, FeeHandlerBRR) | | `campaignID` | uint256 | ID of the campaign | | `startTimestamp` | uint256 | timestamp to start the new campaign | | `endTimestamp` | uint256 | timestamp to end the campaign | | `minPercentageInPrecision` | uint256 | min percentage (in precision) for formula to conclude campaign | | `cInPrecision` | uint256 | c value (in precision) for formula to conclude campaign | | `tInPrecision` | uint256 | t value (in precision) for formula to conclude campaign | | `options` | uint256\[] | list values of options to vote for the campaign | | `link` | bytes | additional data for the campaign | Signature: 0x16cd0674a0f54c4895f5973a1f8f1be4b653af6c2436052d529fd3d0e5def391

\


#### `CancelledCampaign`[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberdao#cancelledcampaign) <a href="#cancelledcampaign" id="cancelledcampaign"></a>

Event for logging the cancellation of a campaign.



event **CancelledCampaign**(uint256 campaignID) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | `campaignID` | uint256 | ID of the campaign | Signature: 0xef29bb5bcfd2b2ff4bc50d710898467757ff87aad1031fc953907b65127f86fc

\


#### Functions[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberdao#functions) <a href="#functions" id="functions"></a>

#### `vote`[​](https://docs.kyberswap.com/Legacy/api-abi/core-smart-contracts/api\_abi-kyberdao#vote) <a href="#vote" id="vote"></a>

Votes for an option of a campaign, where options are indexed from 1 to N number of options.



function **vote**(uint256 campaignID, uint256 option) external override | Parameter | Type | Description | | --------- |:-----:|:-----------:| | `campaignID` | uint256 | ID of campaign | | `option` | uint256 | ID of option |

\
\### \`shouldBurnRewardForEpoch\` Since some epochs have rewards but no one can claim it, return true if those rewards should be burned. \_\_\_ function \_\_shouldBurnRewardForEpoch\_\_(uint256 epoch) external view override returns (bool) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`epoch\` | uint256 | epoch number to check | \*\*Returns:\*\*\ \`true\` if rewards should be burned for the epoch, \`false\` otherwise\
\### \`getListCampaignIDs\` Returns a list of campaign IDs for a given epoch. \_\_\_ function \_\_getListCampaignIDs\_\_(uint256 epoch) external view returns (uint256\[] campaignIDs) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`epoch\` | uint256 | epoch number to query | \*\*Returns:\*\*\ campaignIDs - list of campaign IDs for a given epoch\
\### \`getTotalEpochPoints\` Returns the total epoch points of a given epoch \_\_\_ function \_\_getTotalEpochPoints\_\_(uint256 epoch) external view override returns (uint256) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`epoch\` | uint256 | epoch number to query | \*\*Returns:\*\*\ Total epoch points\
\### \`getCampaignDetails\` Returns the campaign details given a campaign ID. \_\_\_ function \_\_getCampaignDetails\_\_(uint256 campaignID) external view returns (enum KyberDao.CampaignType campaignType, uint256 startTimestamp, uint256 endTimestamp, uint256 totalKNCSupply, uint256 minPercentageInPrecision, uint256 cInPrecision, uint256 tInPrecision, bytes link, uint256\[] options) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`campaignID\` | uint256 | ID of campaign to query | \*\*Returns:\*\*\ campaignType - type of campaign (General, NetworkFee, FeeHandlerBRR) startTimestamp - timestamp of the start the campaign endTimestamp - timestamp to the end the campaign totalKNCSupply - total supply of the KNC token minPercentageInPrecision - min percentage (in precision) for formula to conclude campaign cInPrecision -c value (in precision) for formula to conclude campaign tInPrecision -t value (in precision) for formula to conclude campaign link - list values of options to vote for the campaign options - additional data for the campaign\
\### \`getCampaignVoteCountData\` Returns the number of vote data for a campaign. \_\_\_ function \_\_getCampaignVoteCountData\_\_(uint256 campaignID) external view returns (uint256\[] voteCounts, uint256 totalVoteCount) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`campaignID\` | uint256 | ID of campaign to query | \*\*Returns:\*\*\ voteCounts - array showing the number of votes per option totalVoteCount - total number of votes in the campaign\
\### \`getPastEpochRewardPercentageInPrecision\` Returns the staker's reward percentage in precision for a past epoch only. \_\_\_ function \_\_getPastEpochRewardPercentageInPrecision\_\_(address staker, uint256 epoch) external view override returns (uint256) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`staker\` | address | staker's address | | \`epoch\` | uint256 | past epoch number | \*\*Returns:\*\*\ Past epoch reward percentage in precision for the staker\
\### \`getCurrentEpochRewardPercentageInPrecision\` Returns the staker's reward percentage in precision for the current epoch. Reward percentage is not finalized until the current epoch has ended. \_\_\_ function \_\_getCurrentEpochRewardPercentageInPrecision\_\_(address staker) external returns (uint256) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`staker\` | address | staker's address | \*\*Returns:\*\*\ Current epoch reward percentage in precision for the staker\
\### \`getCampaignWinningOptionAndValue\` Returns the campaign winning option and its value. Returns (0, 0) if the campaign does not exist, the campaign has not ended yet, or the campaign has no winning option based on the formula. \_\_\_ function \_\_getCampaignWinningOptionAndValue\_\_(uint256 campaignID) public view returns (uint256 optionID, uint256 value) | Parameter | Type | Description | | --------- |:-----:|:-----------:| | \`campaignID\` | uint256 | ID of campaign to query | \*\*Returns:\*\*\ optionID - the winning option ID value - the value of the winning option\
\### \`getLatestNetworkFeeData\` Return the latest network fee and expiry timestamp. \_\_\_ function \_\_getLatestNetworkFeeData\_\_() public returns (uint256 feeInBps, uint256 expiryTimestamp)\ \*\*Returns:\*\*\ feeInBps - network fee in BPS expiryTimestamp - the timestamp when the fee will expire and needs to be updated\
\### \`getLatestBRRData\` Returns the latest BRR result. \_\_\_ function \_\_getLatestBRRData\_\_() public view returns (uint256 burnInBps, uint256 rewardInBps, uint256 rebateInBps, uint256 epoch, uint256 expiryTimestamp)\ \*\*Returns:\*\*\ burnInBps - burn ratio in BPS rewardInBps - rewards ratio in BPS rebateInBps - reabtes ratio in BPS epoch - latest epoch expiryTimestamp - the timestamp when BRR values will expire and needs to be updated