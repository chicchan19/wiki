In order to free ethereum implementation developers from the hassle of writing their own JavaScript implementation for browser-to-node communication there's now [ethereum.js](https://github.com/ethereum/ethereum.js).

Ethereum.js provides a full communication bridge between your node (backend) and browser (frontend) given that you **tell** it how _speak_. Communication is done through a `Provider`.

Ethereum.js exports one single container; `web3` which contains the `eth`,`db` and `ssh` object as well as a few helper methods (see [[JavaScript-API]] for more details).

If you have [cpp-ethereum](https://github.com/ethereum/cpp-ethereum), you can start JSONRPC server by typing `eth -j -b`, where `-j` is responsible for starting http server && `-b` for connecting to the default Ethereum peerserver.

### JSON RPC

The following RPC messages should be accepted by the RPC-backend:

* [web3_sha3](#web3_sha3)
* [eth_coinbase](#eth_coinbase)
* [eth_setCoinbase](#eth_setcoinbase)
* [eth_listening](#eth_listening)
* [eth_setListening](#eth_setlistening)
* [eth_mining](#eth_mining)
* [eth_setMining](#eth_setmining)
* [eth_gasPrice](#eth_gasprice)
* [eth_accounts](#eth_accounts)
* [eth_peerCount](#eth_peercount)
* [eth_defaultBlock](#eth_defaultblock)
* [eth_setDefaultBlock](#eth_setdefaultblock)
* [eth_number](#eth_number)
* [eth_balanceAt](#eth_balanceat)
* [eth_stateAt](#eth_stateat)
* [eth_storageAt](#eth_storageat)
* [eth_countAt](#eth_countat)
* [eth_codeAt](#eth_codeat)
* [eth_transact](#eth_transact)
* [eth_call](#eth_call)
* [eth_flush](#eth_flush)
* [eth_blockByHash](#eth_blockbyhash)
* [eth_blockByNumber](#eth_blockbynumber)
* [eth_transactionByHash](#eth_transactionbyhash)
* [eth_transactionByNumber](#eth_transactionbynumber)
* [eth_uncleByHash](#eth_unclebyhash)
* [eth_uncleByNumber](#eth_unclebynumber)
* [eth_compilers](#eth_compilers)
* [eth_lll](#eth_lll)
* [eth_solidity](#eth_solidity)
* [eth_serpent](#eth_serpent)
* [eth_newFilter](#eth_newfilter)
* [eth_newFilterString](#eth_newfilterstring)
* [eth_uninstallFilter](#eth_uninstallfilter)
* [eth_changed](#eth_changed)
* [eth_filterLogs](#eth_filterlogs)
* [eth_logs](#eth_logs)
* [eth_getWork](#eth_getWork)
* [eth_submitWork](#eth_submitWork)
* [db_put](#db_put)
* [db_get](#db_get)
* [db_putString](#db_putstring)
* [db_getString](#db_getstring)
* [shh_post](#shh_post)
* [shh_newIdentity](#shh_newidentity)
* [shh_haveIdentity](#shh_haveidentity)
* [shh_newGroup](#shh_newgroup)
* [shh_addToGroup](#shh_addtogroup)
* [shh_newFilter](#shh_newfilter)
* [shh_uninstallFilter](#shh_uninstallfilter)
* [shh_changed](#shh_changed)


##### `web3_sha3`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"web3_sha3","params":["0x68656c6c6f20776f726c64"],"id":64}' http://localhost:8080
```
* response:
```json
{
"id":64,
"jsonrpc":"2.0",
"result":"0x47173285a8d7341e5e972fc677286384f802f8ef42a5ec5f03bbfa254cb01fad"
}
```

##### `eth_coinbase`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_coinbase","params":[],"id":64}' http://localhost:8080
```
* response:
```json
{
"id":64,
"jsonrpc":"2.0",
"result":"0x407d73d8a49eeb85d32cf465507dd71d507100c1"
}
```

##### `eth_setCoinbase`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_setCoinbase","params":["0x407d73d8a49eeb85d32cf465507dd71d507100c1"],"id":66}' http://localhost:8080
```
* response:
```json
{
"id":66,
"jsonrpc":"2.0",
"result":true
}
```

##### `eth_listening`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_listening","params":[],"id":67}' http://localhost:8080
```
* response:
```json
{
"id":67,
"jsonrpc":"2.0",
"result":true
}
```
##### `eth_setListening`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_setListening","params":[false],"id":68}' http://localhost:8080
```
* response:
```json
{
"id":68,
"jsonrpc":"2.0",
"result":true
}
```
##### `eth_mining`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_mining","params":[],"id":71}' http://localhost:8080
```
* response:
```json
{
"id":71,
"jsonrpc":"2.0",
"result":true
}
```
##### `eth_setMining`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_setMining","params":[false],"id":72}' http://localhost:8080
```
* response:
```json
{
"id":72,
"jsonrpc":"2.0",
"result":true
}
```
##### `eth_gasPrice`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_gasPrice","params":[],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":73,
"jsonrpc":"2.0",
"result":"0x09184e72a000"
}
```
##### `eth_accounts`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_accounts","params":null,"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":["0x407d73d8a49eeb85d32cf465507dd71d507100c1"]
}
```
##### `eth_peerCount`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_peerCount","params":[],"id":74}' http://localhost:8080
```
* response:
```json
{
"id":74,
"jsonrpc":"2.0",
"result":0
}
```
##### `eth_defaultBlock`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_defaultBlock","params":[],"id":77}' http://localhost:8080
```
* response:
```json
{
"id":77,
"jsonrpc":"2.0",
"result":-1
}
```
##### `eth_setDefaultBlock`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_setDefaultBlock","params":[1],"id":80}' http://localhost:8080
```
* response:
```json
{
"id":80,
"jsonrpc":"2.0",
"result":true
}
```
##### `eth_number`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_number","params":[],"id":83}' http://localhost:8080
```
* response:
```json
{
"id":83,
"jsonrpc":"2.0",
"result":1207
}
```
##### `eth_balanceAt`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_balanceAt","params":["0x407d73d8a49eeb85d32cf465507dd71d507100c1"],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":"0x0234c8a3397aab580000"
}
```
##### `eth_stateAt`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_stateAt","params":["0x407d73d8a49eeb85d32cf465507dd71d507100c1", 0],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":"0x03"
}
```
##### `eth_storageAt`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_storageAt","params":["0x407d73d8a49eeb85d32cf465507dd71d507100c1"],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":{"0x":"0x03"}
}
```
##### `eth_countAt`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_countAt","params":["0x407d73d8a49eeb85d32cf465507dd71d507100c1"],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":1
}
```
##### `eth_codeAt`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_countAt","params":["0xd5677cf67b5aa051bb40496e68ad359eb97cfbf8"],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":"0x600160008035811a818181146012578301005b601b6001356025565b8060005260206000f25b600060078202905091905056"
}
```
##### `eth_transact`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_transact","params":[{code:"0x600160008035811a818181146012578301005b601b6001356025565b8060005260206000f25b600060078202905091905056"}],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":"0x7f9fade1c0d57a7af66ab4ead7c2eb7b11a91385"
}
```
##### `eth_call`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_call","params":[{"to":"0xc4abd0339eb8d57087278718986382264244252f","data":"0xc6888fa10000000000000000000000000000000000000000000000000000000000000003"}],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":"0x0000000000000000000000000000000000000000000000000000000000000015"
}
```
##### `eth_flush`
* request:
```bash
```
* response:
```json
```
##### `eth_blockByHash`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_blockByHash","params":["ee670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": {
  "difficulty":"0x0327c5", 
  "extraData":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "gasLimit":300018,
  "hash":"ee670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331",
  "minGasPrice":"0x09184e72a000",
  "miner":"0x82022c34d173cf3b83c6e4553d627276fff6b66d",
  "nonce":"0xc2adfa12f40d142eb585b0b7892cd0841cf30dd18cb88940a5323df767f0db2f",
  "number":1231,
  "parentHash":"0xaa322b7bd7418b4328f0c7b350359a86d6b9b698ef584937447743b082eed099",
  "sha3Uncles":"0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  "stateRoot":"0x86df58f157e5ff5b77a6b1cddb43a2616acbaa7907087e0effb339e14c23a5db",
  "timestamp":1416509555,
  "transactionsRoot":"0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421"
  }
}
```

##### `eth_blockByNumber`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_blockByNumber","params":[1231],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":{
  "difficulty":"0x0327c5",
  "extraData":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "gasLimit":300018,
  "hash":"ee670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331",
  "minGasPrice":"0x09184e72a000",
  "miner":"0x82022c34d173cf3b83c6e4553d627276fff6b66d",
  "nonce":"0xc2adfa12f40d142eb585b0b7892cd0841cf30dd18cb88940a5323df767f0db2f",
  "number":1231,
  "parentHash":"0xaa322b7bd7418b4328f0c7b350359a86d6b9b698ef584937447743b082eed099",
  "sha3Uncles":"0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  "stateRoot":"0x86df58f157e5ff5b77a6b1cddb43a2616acbaa7907087e0effb339e14c23a5db",
  "timestamp":1416509555,
  "transactionsRoot":"0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421"
  }
}
```
##### `eth_transactionByHash`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_transactionByHash","params":[0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b, 0],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": {
  "from":"0x407d73d8a49eeb85d32cf465507dd71d507100c1",
  "gas":520464,
  "gasPrice":"0x09184e72a000",
  "hash":"0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b",
  "input":"0x603880600c6000396000f3006001600060e060020a600035048063c6888fa114601857005b6021600435602b565b8060005260206000f35b600081600702905091905056",
  "nonce":"0x",
  "to":"0x0000000000000000000000000000000000000000",
  "value":"0x"
  }
}
```
##### `eth_transactionByNumber`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_transactionByNumber","params":[668, 0],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": {
  "from":"0x407d73d8a49eeb85d32cf465507dd71d507100c1",
  "gas":520464,
  "gasPrice":"0x09184e72a000",
  "hash":"0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b",
  "input":"0x603880600c6000396000f3006001600060e060020a600035048063c6888fa114601857005b6021600435602b565b8060005260206000f35b600081600702905091905056",
  "nonce":"0x",
  "to":"0x0000000000000000000000000000000000000000",
  "value":"0x"
  }
}
```
##### `eth_uncleByHash`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_uncleByHash","params":["0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b", 0],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": {
  "difficulty":"0x",
  "extraData":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "gasLimit":0,
  "hash":"0000000000000000000000000000000000000000000000000000000000000000",
  "miner":"0x0000000000000000000000000000000000000000",
  "nonce":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "number":0,
  "parentHash":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "sha3Uncles":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "stateRoot":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp":-1,
  "transactionsRoot":"0x0000000000000000000000000000000000000000000000000000000000000000"
  }
}
```
##### `eth_uncleByNumber`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_uncleByNumber","params":[500, 0],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": {
  "difficulty":"0x",
  "extraData":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "gasLimit":0,
  "hash":"0000000000000000000000000000000000000000000000000000000000000000",
  "miner":"0x0000000000000000000000000000000000000000",
  "nonce":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "number":0,
  "parentHash":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "sha3Uncles":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "stateRoot":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp":-1,
  "transactionsRoot":"0x0000000000000000000000000000000000000000000000000000000000000000"
  }
}
```
##### `eth_compilers`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_compilers","params":[],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":["lll", "solidity", "serpent"]
}
```
##### `eth_lll`
* request:
```bash
// TODO
```
* response:
```json
// TODO
```
##### `eth_solidity`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_solidity","params":["contract test { function multiply(uint a) returns(uint d) {   return a * 7;   } }"],"id":1}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":"0x603880600c6000396000f3006001600060e060020a600035048063c6888fa114601857005b6021600435602b565b8060005260206000f35b600081600702905091905056"
}
```
##### `eth_serpent`
* request:
```bash
// TODO
```
* response:
```json
// TODO
```
##### `eth_newFilter`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newFilter","params":[{"topic":"0x12341234"}],"id":73}' http://localhost:8080
```
* response:
```json
```
##### `eth_newFilterString`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newFilterString","params":["pending"],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": 1
}
```
##### `eth_uninstallFilter`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_uninstallFilter","params":[0],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": true
}
```
##### `eth_changed`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_changed","params":[0],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": [{
  "address":"0x0000000000000000000000000000000000000000",
  "data":"0x0000000000000000000000000000000000000000000000000000000000000000",
  "number":0
  }]
}
```
##### `eth_filterLogs`
* request:
```bash
// TODO
```
* response:
```json
// TODO
```
##### `eth_logs`
* request:
```bash
// TODO
```
* response:
```json
// TODO
```
##### `eth_getWork`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getWork","params":[],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": "0x1234567890abcdef1234567890abcdef"
}
```
##### `eth_submitWork`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_submitWork","params":["0x1234567890abcdef1234567890abcdef"],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": 1
}
```
##### `db_put`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"db_put","params":["test","key","5"],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": true
}
```
##### `db_get`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"db_get","params":["test","key"],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": "0x05"
}
```
##### `db_putString`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"db_putString","params":["test","key","5"],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": true
}
```
##### `db_getString`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"db_getString","params":["test","key"],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": "5"
}
```
##### `shh_post`
* request:
```bash
"0x68656c6c6f20776f726c64"
curl -X POST --data '{"jsonrpc":"2.0","method":"db_getString","params":[{"from":"0xc931d93e97ab07fe42d923478ba2465f283f440fd6cabea4dd7a2c807108f651b7135d1d6ca9007d5b68aa497e4619ac10aa3b27726e1863c1fd9b570d99bbaf","topic":"0x68656c6c6f20776f726c64","payload":"0x68656c6c6f20776f726c64","ttl":100,"priority":100}],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": true
}
```
##### `shh_newIdeninty`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"ssh_newIdentity","params":[],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result":"0xc931d93e97ab07fe42d923478ba2465f283f440fd6cabea4dd7a2c807108f651b7135d1d6ca9007d5b68aa497e4619ac10aa3b27726e1863c1fd9b570d99bbaf"
}
```
##### `shh_haveIdentity`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"ssh_haveIdentity","params":["0xc931d93e97ab07fe42d923478ba2465f283f440fd6cabea4dd7a2c807108f651b7135d1d6ca9007d5b68aa497e4619ac10aa3b27726e1863c1fd9b570d99bbaf"],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": true
}
```
##### `shh_newGroup`
* request:
```bash
// TODO: not implemented yet
```
* response:
```json
// TODO: not implemented yet
```
##### `shh_addToGroup`
* request:
```bash
// TODO: not implemented yet
```
* response:
```json
// TODO: not implemented yet
```
##### `shh_newFilter`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_newFilter","params":[{"topic":"0x68656c6c6f20776f726c64"}],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": 7
}
```
##### `shh_uninstallFilter`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_uninstallFilter","params":[7],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": 7
}
```
##### `shh_changed`
* request:
```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_uninstallFilter","params":[7],"id":73}' http://localhost:8080
```
* response:
```json
{
"id":1,
"jsonrpc":"2.0",
"result": [{
  "expiry":1422565026,
  "from":"0x3ec052fc3376f8a218b24b652803a5892038c39419a9a44923a61b113b7785d16ed1572df628859af3504670e4df31dcd8b3ee9a2110fd710c948690f0557394",
  "hash":"0x33eb2da77bf3527e28f8bf493650b1879b08c4f2a362beae4ba2f71bafcd91f9",
  "payload":"0x7b2274797065223a226d657373616765222c2263686174223a2265537668624d763939784c345442537741222c2274696d657374616d70223a7b222464617465223a313432323536343932363533377d2c22746f706963223a22222c2266726f6d223a7b226964656e74697479223a2230783365633035326663333337366638613231386232346236353238303361353839323033386333393431396139613434393233613631623131336237373835643136656431353732646636323838353961663335303436373065346466333164636438623365653961323131306664373130633934383639306630353537333934222c226e616d65223a22416365746f7465227d2c226d657373616765223a2273617361222c226964223a227a465232614e68594a666f4d4c62707333227d",
  "sent":1422564926,
  "to":"0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "topics":["0x6578616d"],
  "ttl":100,
  "workProved":0
  }]
}
```

Questions? @marek