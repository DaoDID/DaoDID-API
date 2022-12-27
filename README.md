# DaoDID-API
this is a open API for manage DaoDID service and authing requiring

General API Information
The base endpoint is: https://daodid.id/api/


### Get Authing level

#### Request

* path: /authing/check
* Query Params: 
  
  sAccount:  2077.bit

  sAddress:  0x229a1d58d9745ea9ce762d39ae9062323a11eac4

#### Response

User who doesn't own any subaccount or neither paid, will be labeled as no_auth with authority value: -1
```json
{
    "err_no": 1,
    "err_msg": "fail",
    "data": {
        "sAddress": "0xc4091AF0ad28b1964F5eea9C3827b815c8c86F3B",
        "sAccount": "2077.bit",
        "authing": -1,
        "role": "no_auth"
    }
}
```

once user paid, it will be list in waiting room with default authority value: 1 
```json
{
    "err_no": 0,
    "err_msg": "ok",
    "data": {
        "sAddress": "0xa5069d5a768766684C098E28b10eC9b369953823",
        "sAccount": "2077.bit",
        "authing": 1,
        "role": "waiting_room"
    }
}
```

User owns subaccount will be labeled as: subscriber with authority value 1-99. 
```json
{
    "err_no": 0,
    "err_msg": "ok",
    "data": {
        "sAddress": "0x229a1d58d9745ea9ce762d39ae9062323a11eac4",
        "sAccount": "2077.bit",
        "authing": 10,
        "role": "subscriber"
    }
}
```
* authing：1-99 higher value, higher authority. Parent account owner can define authority value for each specific subaccount on DaoDID control pannel. (default value for subscriber is 1)







### Check if account opened for public
* path: /authing/opened
* Query Params: 
  
  sAccount:  2077.bit
  
  #### Response

```json
{
    "err_no": 0,
    "err_msg": "ok",
    "data": {
        "isOpened": true,
        "priceProfile": [
            {
                "iPrefixLenStart": 1,
                "iPrefixLenEnd": 10
            },
            {
                "iPrefixLenStart": 11,
                "iPrefixLenEnd": 11
            },
            {
                "iPrefixLenStart": 12,
                "iPrefixLenEnd": 12
            },
            {
                "iPrefixLenStart": 13,
                "iPrefixLenEnd": 13
            }
        ]
    }
}
```
* priceProfile shows the price config for all available prefix length
