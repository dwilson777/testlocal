# The Ad Data Model
The Ad Data Model is described in detail below:

| property | default | type | description | example | possible values |
| -------- | ------- | ---- | ----------- | ------- | --------------- |
| id | `null` | String | An ad server defined identifier string for the ad. Consists of the 3 parts (separated by `-`) `adOrderId`, `adLineitemId` and `adCreativeId`. | `'55555-12345-77777'` ||
| positionName | `null` | String | The name of the position in a roll. | `'preroll1b'` ||
| rollName | `null` | String | The name of the roll, e.g. preroll. | `'preroll'` ||
| rollIndex | `0` | uint | The index of a roll like an interstitial at midroll - 2. | `1` ||
| adGapId | `null` | String | A manually managed ad id, that is provided as VAST extension from external ad servers (wrappers). | `'AdGapId_021_800009_16439001-11000;'` ||

