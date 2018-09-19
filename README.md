# Exexnium trade public API

**Note, that this is beta-mode of public api and we will develop some change in next few months.**

Base API URL: 
https://api.exenium.io


## SYMBOL list

Returns available trade SYMBOLS

```
GET /trade/pair/list?page=1&size=5
```

```json
{
  "items":[
    {"currency_codes":["ETH","BTC"]},
    {"currency_codes":["DASH","BTC"]},
    {"currency_codes":["XNT","BTC"]},
    {"currency_codes":["XNT","DASH"]},
    {"currency_codes":["BTC","USD"]}
  ],
  "start":0,
  "total":15
}
```

#### GET parametes

 parameter | type | description
--- |--- | ---
 page | number | [optional] Number of page (from 0), deafult 0 
 size | number | [optional] Size of page (from 1 to 100), default 20

#### Return values

 parameter | type | description
--- |--- | ---
 items | array | Array of available SYMBOLs
 items[] | object | SYMBOL
 items[].currency_codes | array | Array of SYMBOL currencies
 items[].currency_codes[] | string | Code of currency
 start | number | Number of first element in returned array `items`
 total | number | Total resulted elements available for current method
 

## SYMBOL info

Returns trade info for requested SYMBOL

```
GET /trade/pair/info?currencies=BTC,USD
```

```json
{
  "volume24h":648949.124155282600000000,
  "price":6357.700657333333333333,
  "change1h":0.996898150000000000,
  "change24h":1.010710900000000000,
  "change1w":1.007424030000000000,
  "high24h":6458.264453587934379961,
  "low24h":6267.512030797940797941,
  "currency_codes":["BTC","USD"],
  "ask_price":6363.495280000000000000,
  "ask_amount":0.004790000000000000,
  "bid_price":6357.688560000000000000,
  "bid_amount":0.003110000000000000
  }
```

#### GET parametes

 parameter | type | description
--- |--- | ---
 currencies | number | [required] SYMBOL currencies
 
 
 ## SYMBOL orders

Returns orders of SYMBOL

```
GET /trade/pair/order/list?pair=BTC,USD&page=0
```

```json
[
  {"rate":6281.2202800000000000,"order_type":"BUY","current_amount":0.0823900000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6315.4243400000000000,"order_type":"BUY","current_amount":0.0823600000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6323.4657500000000000,"order_type":"BUY","current_amount":0.0503900000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6330.5882000000000000,"order_type":"BUY","current_amount":0.0030200000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6330.6094700000000000,"order_type":"BUY","current_amount":0.0022800000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6343.2118100000000000,"order_type":"BUY","current_amount":0.0008300000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6345.6703200000000000,"order_type":"BUY","current_amount":0.0003100000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6346.5516700000000000,"order_type":"BUY","current_amount":0.0002600000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6348.7241900000000000,"order_type":"BUY","current_amount":0.0000200000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6349.6743300000000000,"order_type":"BUY","current_amount":0.0000100000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6354.8199300000000000,"order_type":"SELL","current_amount":0.0001300000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6356.0840800000000000,"order_type":"SELL","current_amount":0.0001600000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6356.1482600000000000,"order_type":"SELL","current_amount":0.0002000000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6360.0552400000000000,"order_type":"SELL","current_amount":0.0002500000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6360.0804800000000000,"order_type":"SELL","current_amount":0.0002900000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6361.6444300000000000,"order_type":"SELL","current_amount":0.0003000000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6363.4952800000000000,"order_type":"SELL","current_amount":0.0050900000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6369.6065700000000000,"order_type":"SELL","current_amount":0.0051100000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6370.2004600000000000,"order_type":"SELL","current_amount":0.0052300000000000,"currency_code1":"BTC","currency_code2":"USD"},
  {"rate":6370.5299900000000000,"order_type":"SELL","current_amount":0.0054600000000000,"currency_code1":"BTC","currency_code2":"USD"}
]
```

#### GET parametes

 parameter | type | description
--- |--- | ---
 pair | string | [required] currencies of symbol, divided by ","
 page | number | [required] page of list. From -10 (for BUY orders) to 10 (for SELL orders). If zero - return 10 best SELL and 10 best BUY orders.
 
 
