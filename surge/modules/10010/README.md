# èéä½é

<table style="padding: 10px">

  <tr>
    <td><img src="https://i.loli.net/2021/07/24/XeZEUqbjJgC7RFV.jpg" width="400px"></td>
    <td><img src="https://i.loli.net/2021/07/24/yYrJmK7znEwiDsT.jpg" width="400px"></td>
  </tr>
   <tr>
    <td><img src="https://i.loli.net/2021/07/24/JWC21sOSPrp3duR.jpg" height="200px" width="200px"></td>
  </tr>
</table>

> ð èéä½é(v2)

v2 çæ¬ä½¿ç¨ [OpenAPI](https://github.com/Peng-YM/QuanX/tree/master/Tools/OpenAPI), so WORA.

æ°ç¹æ§:

- å¤è´¦å·

- åæ­¥éç½®è³ V2P

- èªå¨ç»å½

- æ´å¤èªå®ä¹é¡¹

  - `free_pkg(åæµæµéååæ­£å)` å `exclude_remain_pkg(ä¸è®¡ç®å©ä½æµéçæµéååæ­£å)` ç®è¦è¯´æ(å­æ®µè¯´æ ä»¥ [BoxJs éç½®é¡¹](https://github.com/xream/scripts/blob/main/boxjs/boxjs.json)ä¸ºå)

    - é¨åç¨æ·åé¦å°éå¼å¯å¡ååæµæ¾ç¤ºå¼å¸¸. å ä¸ºèéæªå°ééå®åè®¡å¥åæµå­æ®µ. éè®¾ç½® `free_pkg(åæµæµéååæ­£å)` å `exclude_remain_pkg(ä¸è®¡ç®å©ä½æµéçæµéååæ­£å)` ä¸º `(ééå®ååæµèµè´¹|å¥é¤åä¸äº«åè´¹æµé)`

    - æµé¦æç±»ä¼¼çå¥é¤ éè¦è®¾ç½® `exclude_remain_pkg(ä¸è®¡ç®å©ä½æµéçæµéååæ­£å)` ä¸º `(å¤´æ¡ç³»APPåæµ|å¥é¤åä¸äº«åè´¹æµé)`

æ³¨æäºé¡¹:

- è®¾ç½®ä¸­ç `å å¯æ¥å£` ç¨äºå¨é Node ç¯å¢ä¸­å å¯ææºå·åå¯ç , å¯æå¼ [rsapublickeyencode](https://runkit.com/xream/rsapublickeyencode) èªå·±é¨ç½²/Clone åç¹å» endpoint å¾å°å°å, å¡«å¥è®¾ç½®

## æäºº Surge Module

ð [èéä½é(v2)](https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010v2.sgmodule)

## æå¨è®¾ç½® Scripts

### ð èéä½é(v2)

```
[MITM]
hostname = m.client.10010.com

[Script]
# Surge
èéä½é: Cookie = type=http-request,pattern=^https?:\/\/m\.client\.10010\.com\/(servicequerybusiness\/operationservice\/queryOcsPackageFlowLeftContent|servicequerybusiness\/balancenew\/accountBalancenew\.htm|mobileService\/onLine\.htm),requires-body=1,max-size=0,timeout=30,script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js,debug=true
èéä½é: æ¥è¯¢ = type=cron,cronexp=*/5 * * * *,timeout=30,script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js,wake-system=true

# Loon
http-request ^https?:\/\/m\.client\.10010\.com\/(servicequerybusiness\/operationservice\/queryOcsPackageFlowLeftContent|servicequerybusiness\/balancenew\/accountBalancenew\.htm|mobileService\/onLine\.htm) script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js, requires-body=true, timeout=10, tag=èéä½éCookie
cron "*/5 * * * *" script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js

# QuanX(æªæµè¯ ä¸æ¸æ¥å¦ä½å¤æ­å½åç½ç»æ¯å¦ä¸º WiFi)
^https?:\/\/m\.client\.10010\.com\/(servicequerybusiness\/operationservice\/queryOcsPackageFlowLeftContent|servicequerybusiness\/balancenew\/accountBalancenew\.htm|mobileService\/onLine\.htm) url script-request-body https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js
*/5 * * * * https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js, tag=èéä½éæ¥è¯¢
```

## BoxJs è®¢é

ä½¿ç¨ [BoxJs æµè¯ç](https://chavyleung.gitbook.io/boxjs) æ·»å  [è®¢é](https://raw.githubusercontent.com/xream/scripts/main/boxjs/boxjs.json) å, Scriptable èæ¬å¯æ¯æç¼å­ Cookie

å¯è®¾ç½®:

- ä½¿ç¨ WiFi æ¶, ä¹è¿è¡æ£æ¥(Surge/Loon é»è®¤ä¸æ£æ¥; å¶ä» app æ»æ¯æ£æ¥)

- å½åæ¶é´æ®µåæ ç¨éæ¶, ä¹è¿è¡éç¥(é»è®¤ä¸éç¥)

- è·å cookie æ¶, èªå¨éè¿ V2P webhook åæ­¥ cookie

<table style="padding: 10px">
  <tr>
    <td><img src="https://i.loli.net/2021/07/25/ApmGUxL5ujTwkBn.jpg" height="600px"></td>
    <td><img src="https://i.loli.net/2021/07/25/ApmGUxL5ujTwkBn.jpg" height="600px"></td>
  </tr>
</table>

## è·å Cookie

ç»å½ä¸­å½èé app, æå¼ä½éæ¥è¯¢, è·å Cookie

## V2P

### ð èéä½é(v2)

å¨ `TASK(å®æ¶ä»»å¡)` ä¸­, ç¹å»`æ·»å åä¸ªä»»å¡`, è®¾ç½® `èéä½é`, `cronå®æ¶`, `30 */5 * * * *`, `è¿è¡JS`, `https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js`

#### éç½®

æ­£ç¡®è®¾ç½® BoxJs å, Cookie æ´æ°æ¶å°èªå¨åæ­¥æ°æ®å° V2P.

éè¿å¯ç¨ `V2P æ¯å¦å¨ç´æ¥æ§è¡èæ¬æ¶åæ­¥ä¸æ¬¡` å¹¶ä¿å­, åæå¨æ§è¡èæ¬å®ç°åæ¬¡åæ­¥

ä¹å¯å¨ `JSMANAGE(JS æä»¶ç®¡ç)` ä¸­ç `store/cookie å¸¸éå¨å­ç®¡ç` ä¸­æå¨è®¾ç½®, åèä»¥ä¸åå®¹(å­æ®µè¯´æ ä»¥ [BoxJs éç½®é¡¹](https://github.com/xream/scripts/blob/main/boxjs/boxjs.json)ä¸ºå ), èªè¡è®¾ç½® KEY å VALUE å³å¯

```JSON
{
  "ignore_flow": "10",
  "same": "false",
  "no_url": "true",
  "v2p_disabled": "false",
  "name": "@xream ç±³ç²",
  "maintenance_disabled": "true",
  "cookie_notification_disabled": "false",
  "autoSign": "true",
  "mobile": "",
  "password": "",
  "appId": "",
  "rsapublicKeyEncodeAPI": "https://rsapublickeyencode-kesbkwnyc07x.runkit.sh/",
  "other_pkg": "(æ¥ç§|å­¦ä¹ å¼ºå½)",
  "exclude_remain_pkg": "(å­¦ä¹ å¼ºå½ååå®åæµé|å¥é¤åä¸äº«åè´¹æµé)",
  "free_pkg": "(ééå®ååæµèµè´¹|å¥é¤åä¸äº«åè´¹æµé)",
  "cookie_disabled": "false",
  "device": {
    "deviceOS": "",
    "deviceBrand": "",
    "deviceModel": "",
    "buildSn": "",
    "deviceId": ""
  },
  "encoded": {
    "mobile": "",
    "password": "",
    "original": {
      "mobile": "",
      "password": ""
    }
  },
  "last": {},
  "cookie": ""
}
```

#### å¤è´¦å·ä½¿ç¨

é»è®¤èæ¬ä¸º `10010_query.js`, ä½¿ç¨ store ä¸­ç `10010_query`.

å¦ä¸å°è®¾å¤ä¸, åºå¨ BoxJs ä¸­è®¾ç½® `èªå®ä¹åç§°(é»è®¤ä¸ºå¥é¤å)` ä»¥åºåä¸åè´¦å·çéç¥, è®¾ç½® `V2P store/cookie å¸¸éå¨å­ key` ä¸ºä¸åäº `10010_query` çå¼, ä¾å¦: `YAA`

```JSON
[
  {
    "id": "@10010_query.name",
    "name": "èªå®ä¹åç§°(é»è®¤ä¸ºå¥é¤å)",
    "val": "",
    "type": "text",
    "desc": ""
  },
  {
    "id": "@10010_query.v2p.store.key",
    "name": "V2P store/cookie å¸¸éå¨å­ key",
    "val": "",
    "type": "text",
    "desc": "é»è®¤ä¸º 10010_query"
  }
]
```

å¨è®¾å¤ä¸è¿è¡ä¸æ¬¡åæ­¥, æ­¤æ¶å°åæ­¥ key ä¸º `YAA` ç store è³ V2P.

å¨ V2P ä¸, ä¸ä¼ æä¿å­èæ¬ `10010_query.js` çåå®¹, å½åä¸º `__YAA__10010_query.js`.

ä¹å, èæ¬ `__YAA__10010_query.js` æ§è¡æ¶, ä¼èªå¨ä»èæ¬åä¸­è·å store key å `YAA` å¹¶ä½¿ç¨.

## éé¾

æååç¬æä»¶ `ql raw https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010_query.js`

è®¾ç½®å®æ¶ä»»å¡ `task raw_10010_10010_query.js`

éç½®æä»¶ `10010_query.json`

åèä»¥ä¸åå®¹(å­æ®µè¯´æ ä»¥ [BoxJs éç½®é¡¹](https://github.com/xream/scripts/blob/main/boxjs/boxjs.json)ä¸ºå ), èªè¡è®¾ç½® KEY å VALUE å³å¯

æ³¨æ: éé¾ ä¸º Node ç¯å¢, ä¸æä¾ `rsapublicKeyEncodeAPI` å å¯æ¥å£æ¶, èªå¨è¿è¡æ¬å°å å¯

```JSON
{
  "ignore_flow": "10",
  "same": "false",
  "no_url": "true",
  "v2p_disabled": "false",
  "name": "@xream ç±³ç²",
  "maintenance_disabled": "true",
  "cookie_notification_disabled": "false",
  "autoSign": "true",
  "mobile": "",
  "password": "",
  "appId": "",
  "rsapublicKeyEncodeAPI": "https://rsapublickeyencode-kesbkwnyc07x.runkit.sh/",
  "other_pkg": "(æ¥ç§|å­¦ä¹ å¼ºå½)",
  "exclude_remain_pkg": "(å­¦ä¹ å¼ºå½ååå®åæµé|å¥é¤åä¸äº«åè´¹æµé)",
  "free_pkg": "(ééå®ååæµèµè´¹|å¥é¤åä¸äº«åè´¹æµé)",
  "cookie_disabled": "false",
  "device": {
    "deviceOS": "",
    "deviceBrand": "",
    "deviceModel": "",
    "buildSn": "",
    "deviceId": ""
  },
  "encoded": {
    "mobile": "",
    "password": "",
    "original": {
      "mobile": "",
      "password": ""
    }
  },
  "last": {},
  "cookie": ""
}
```

#### å¤è´¦å·ä½¿ç¨

æ°å»ºä¸ä¸ªèæ¬ `__miku__10010_query.js`, å¹¶å°åèæ¬ `10010_query.js` ä¸­çåå®¹å¤å¶è¿æ¥.

æ°å»º `miku.json` æè¿è¡ä¸æ¬¡ `__miku__10010_query.js` èªå¨çæ `miku.json`

ç¼è¾ `miku.json`

è¥è¦å®ç°å¤è´¦å·ä½¿ç¨ä¸åçéç¥æ¹å¼, å¯åèå¦ä¸æä½:

ä¾å¦, é»è®¤ä½¿ç¨çæ¯éé, ç°å¨å¸æè´¦å· miku ä½¿ç¨ Bark.

å¯ä»¥å¨ `__miku__10010_query.js` æä¸æ¹æ·»å å¦ä¸ä»£ç :

```JavaScript
process.env.DD_BOT_TOKEN=undefined
process.env.DD_BOT_SECRET=undefined

process.env.BARK_PUSH="https://api.day.app/123456789"
```

æææ¯æ¸é¤é»è®¤çééçç¯å¢åé, å¹¶è®¾ç½® Bark çç¯å¢åé

#### éç½®

æ­£ç¡®è®¾ç½® BoxJs å, Cookie ä¼èªå¨åæ­¥å° V2P

å¶ä»éç½®å¯å¨ `JSMANAGE(JS æä»¶ç®¡ç)` ä¸­ç `store/cookie å¸¸éå¨å­ç®¡ç` ä¸­æå¨è®¾ç½®, åèä»¥ä¸åå®¹(å­æ®µè¯´æ ä»¥ [BoxJs éç½®é¡¹](https://github.com/xream/scripts/blob/main/boxjs/boxjs.json)ä¸ºå ), èªè¡è®¾ç½® KEY å VALUE å³å¯

```JSON
{
  "ignore_flow": "10",
  "same": "false",
  "no_url": "true",
  "v2p_disabled": "false",
  "name": "@xream ç±³ç²",
  "maintenance_disabled": "true",
  "cookie_notification_disabled": "false",
  "autoSign": "true",
  "mobile": "",
  "password": "",
  "appId": "",
  "rsapublicKeyEncodeAPI": "https://rsapublickeyencode-kesbkwnyc07x.runkit.sh/",
  "other_pkg": "(æ¥ç§|å­¦ä¹ å¼ºå½)",
  "exclude_remain_pkg": "(å­¦ä¹ å¼ºå½ååå®åæµé|å¥é¤åä¸äº«åè´¹æµé)",
  "free_pkg": "(ééå®ååæµèµè´¹|å¥é¤åä¸äº«åè´¹æµé)",
  "cookie_disabled": "false",
  "device": {
    "deviceOS": "",
    "deviceBrand": "",
    "deviceModel": "",
    "buildSn": "",
    "deviceId": ""
  },
  "encoded": {
    "mobile": "",
    "password": "",
    "original": {
      "mobile": "",
      "password": ""
    }
  },
  "last": {},
  "cookie": ""
}
```

## Scriptable

> ç®åä»å¯ç¨ æåç»´æ¤ æ¬¢è¿ PR

## èæ¬

ä¾èµ: [ãå°ä»¶ä»¶ãå¼åç¯å¢.js](https://raw.githubusercontent.com/xream/scripts/main/scriptable/ãå°ä»¶ä»¶ãå¼åç¯å¢.js)

[èéä½é.js](https://raw.githubusercontent.com/xream/scripts/main/scriptable/10010/èéä½é.js)

<table style="padding: 10px">
  <tr>
    <td><img src="https://i.loli.net/2021/07/22/vFj9uLMp6BbZmWP.jpg" height="200px"></td>
    <td><img src="https://i.loli.net/2021/07/22/3mnxdtJ8TFMfazu.jpg" height="200px"></td>
  </tr>
</table>
