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

```json
{
    "err_no": 0,
    "err_msg": "ok",
    "data": {
        "sAddress": "0x229a1d58d9745ea9ce762d39ae9062323a11eac4",
        "sAccount": "2077.bit",
        "authing": 1,
        "role": "subscriber"
    }
}
```

* authing：1-99 higher value, higher authority. User can define authority value on DaoDID control pannel. (default value for subscriber: 1)


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
