Public repo for smartcountry.group
=======

Api reference
=======

Firstly you need get API KEY from your smartcountry.group account profile.

Request url format is https://api.smartcountry.group/?key=[YOUR_API_KEY]. Use http POST request with JSON body.

Request JSON message format:

```
{"method":"[METHOD_NAME]"}
```
All methods descriptions are below.

Response JSON format:

```
{
  "result": true,
  "data": {
     [RESPONSE_DATA_OBJECT]
  }
}
```

NOTE Make sure you using valid UserAgent header string in the requests. You may get error 403 from CloudFlare otherwise.

Available Methods
=======

coins_list
-----------

Return all available coins on th pool

Request JSON message:
```
{"method":"coins_list"}
```

Response JSON message example:
```
{
	"result": true,
	"data": [{
		"id": 1,
		"coin": "ETH",
		"description": "Ethereum",
		"coinIconUrl": "https://smartcountry.group/img/eth.png",
		"siteUrl": "https://ethereum.org/",
		"pendingBlockNumber": 14878211,
		"active": true,
		"workersCount": "16",
		"workersHashrate": "2864663729",
		"blockTime": "32.8",
		"networkDifficulty": "14701000000",
		"networkHashrate": "117000000000",
		"baseReward": "2.0",
		"priceBtc": "9718",
		"priceUsd": "0.688",
		"blockRevenueUsd": "4000.9",
		"profit": {
			"hashrate": 1000000000,
			"minutes": 1440,
			"coins":38.1,
			"revenue_usd":23.42
		},
		"workers": {
			"workers_solo": 11,
			"hashrate_solo": 2330542441,
			"workers_pplnt": 1,
			"hashrate_pplnt": 84089713,
			"workers_grouped": 4,
			"hashrate_grouped": 450031575
		}
	}]
}
```
NOTE Fields workersCount and workersHashrate are deprecated and may be removed


coins_reward
blocks_list
workers_summary
workers_hashrate
workers_list
mining_list
change_mining