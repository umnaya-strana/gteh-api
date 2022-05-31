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
		"priceBtc": "62259",
		"priceUsd": "2000.0",
		"blockRevenueUsd": "4000.0",
		"profit": {
			"hashrate": 1000000000,
			"minutes": 1440,
			"coins":0.71,
			"revenue_usd":1420.0
		},
		"workers": {
			"workers_solo": 0,
			"hashrate_solo": 0,
			"workers_pplnt": 320,
			"hashrate_pplnt": 800004089713,
			"workers_grouped": 0,
			"hashrate_grouped": 0
		}
	}]
}
```
NOTE Fields workersCount and workersHashrate are deprecated and may be removed

coins_reward
-----------

Return your coins statistics

Request JSON message:
```
{"method":"coins_reward"}
```

Response JSON message example:
```
{
	"result": true,
	"data": [{
		"coin": "AKA",
		"coinIconUrl": "https://smartcountry.group/img/aka.png",
		"balance": "660139294886",
		"balanceImmature": "75300651",
		"reward": "662014671137",
		"reward24h": "4696017278",
		"blockCount": "897",
		"rewards": {
			"balance_usd": 1508.07740052949,
			"balance_btc": 16449692,
			"reward_usd": 1512.36166684046,
			"reward_btc": 16497040,
			"immature_usd": 0.172023103151084,
			"immature_btc": 0,
			"reward24h_usd": 10.7279745113049,
			"reward24h_btc": 114632
		}
	}]

}
```

blocks_list
-----------

Display last blocks, found on the pool.

Request JSON message:

```
{"method":"blocks_list"}
```

Response JSON message example:
```
{
	"result": true,
	"data": [{
		"id": 300484,
		"blockNumber": 305159,
		"nonce": "0xe0efad403c5715eb",
		"coin": "ETI",
		"coinIconUrl": "http://comining.io/img/eti.png",
		"mining": "ETI / 10G / SOLO",
		"miningUniq": "MINING_UNIQ",
		"status": "Submitted",
		"created": "2018-03-31T17:22:58",
		"worker": "john",
		"workerUniq": "WORKER_UNIQ"
	} 
	...
	]
}
```

workerUniq - unique worker identificator on the pool (you can get it from workers_list)
miningUniq - identificator of mining configuration (you can get it from mining_list)

workers_summary
-----------

Display summary information about workers, grouped by coins

Request JSON message:

```
{"method":"workers_summary"}
```

Response JSON message example:
```
{
	"result": true,
	"data": [{
		"coin": "ETP",
		"coinName": "Metaverse",
		"coinAlgo": "ETHASH",
		"coinIconUrl": "http://comining.io/img/etp.png",
		"workers": "21",
		"workersOffline": "0",
		"workersHashrate": "5152098449",
		"accountLuck":"29%"
	}]
}
```

workers_hashrate
-----------



workers_list
-----------
Display all workers for your account, registered on the pool

Request JSON message:
```
{"method":"workers_list"}
```

Response JSON message example:
```
{
	"result": true,
	"data": [{
		"uniq": "WORKER_UNIQ_1",
		"name": "miner20",
		"description": "sapp gig",
		"status": false,
		"sharesValid1h": 0,
		"sharesInvalid1h": 0,
		"logins24h": 0,
		"loginLast": "2018-03-31T16:42:24",
		"updated": "2018-03-31T17:22:19",
		"hashrate": 256822820,
		"coin": "ETP",
		"coinIconUrl": "http://comining.io/img/etp.png",
		"coinAlgo": "ETHASH",
		"mining": "ETP / 5G / PPLNT",
		"miningUniq": "MINING_UNIQ_1"
	}
        ...
	{
		"uniq": "WORKER_UNIQ_2",
		"name": "miner19",
		"description": "gig",
		"status": false,
		"sharesValid1h": 0,
		"sharesInvalid1h": 0,
		"logins24h": 0,
		"loginLast": "2018-03-30T15:58:57",
		"updated": "2018-03-31T17:23:05",
		"hashrate": 298009065,
		"coin": "ETP",
		"coinIconUrl": "http://comining.io/img/etp.png",
		"coinAlgo": "ETHASH",
		"mining": "ETP / 5G / PPLNT",
		"miningUniq": "MINING_UNIQ_2"
	}]
}
```

uniq - unique worker identificator on pool
miningUniq - identificator of mining configuration (you can get it from mining_list)

Example:
```
curl -d '{"method":"workers_list"}' -H 'Content-Type: application/json' -X POST 'https://api.comining.io/?key=YOUR_KEY'
```

mining_list
-----------
Display all mininig configurations, availble on the pool.

Request JSON message:
```
{"method":"mining_list"}
```

Response JSON message example:
```
{
	"result": true,
	"data": [{
		"uniq": "MSPzcL8yuKEyE6zKhoFp4Vy",
		"mining": "AKA / 10G / SOLO",
		"coin": "AKA",
		"coinIconUrl": "http://comining.io/img/aka.png"
	},
        .....
	{
		"uniq": "MJDAcdzRpqBMPUYtWJSavAZ",
		"mining": "AKA / 5G / PPLNT",
		"coin": "AKA",
		"coinIconUrl": "http://comining.io/img/aka.png"
	}]
}
```
uniq - identificator of mining configuration