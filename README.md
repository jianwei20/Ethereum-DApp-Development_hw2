# Homework 1

## 作業繳交
:warning: 注意
- Deadline: 10/30 (before 11:59pm)
- How to submit? Register an account on  https://github.com/ and push your code and the answer there. For question 2, please attach your source code.
- Last, submit your repo url to the coursework via https://classroom.google.com/u/0/c/MTE2MzEyMzM4NjRa.
:::


## 作業環境

> 不限程式語言


1. 安裝 Node.js
2. 安裝下列套件

```javascript
$ npm install ethereumjs-wallet
$ npm install js-sha3
```

3. 測試是否執行成功

開一個檔案將下列程式碼存在 `key.js`


```javascript=
// npm-library
const Wallet = require('ethereumjs-wallet');
const keccak256 = require('js-sha3').keccak256;

// keypair
const wallet = Wallet.generate();
 
// privKey
const privKey = wallet.getPrivateKey();
console.log("privKey:", privKey);
 
// pubKey
const pubKey = wallet.getPublicKey();
console.log("pubKey:", pubKey);

// address
let address = wallet.getAddressString();
console.log("address:", address);
```

執行 `key.js`，若看到下列畫面表示成功

```
$ node key.js

privKey: <Buffer c7 49 b3 89 eb c3 28 3f 2e 52 5f fe 46 93 70 ed 37 64 85 1a 24 81 6d 56 54 cd 9d 99 f2 c1 2e f6>
pubKey: <Buffer 30 92 f7 ed ac aa 49 e0 f1 74 ea 63 53 ce be 65 aa 3f 73 32 18 51 62 cc 00 2f 23 9b 35 86 58 83 d7 bc c6 fd 49 69 b8 80 45 91 32 fe 6d c1 9d fa 6d 64 ... >
address: 0x759c946e5306e7e6498f4286055a931fe7b08882
```

- 註：Windows 10 作業系統建置 Node.js 開發環境可參考此[連結](/c/S1V4HngYX/%2FUzEjDQFdTQuEjhtVdaNcXg)。

---


## 作業描述

#### (20%) 1. Please compare hash function and cryptographic hash function and give an example.


#### (80%) 2. Peter is a noob in cryptocurrency and would like to get some Ethers. First step for him is to have an Ethereum account. He decides to generate an account and manages the wallet himself so he can understand the principles behind. From the class, he knows the account is created by the following steps:

   1.	Create a keypair of private/public key
   2.	public_key = ECDSA(private_key) 
   3.	public_key_hash = Keccak-256(public_key)
   4.	address = `'0x'` + last 20 bytes of public_key_hash


#### Reference 

- [Create Full Ethereum Wallet, Keypair and Address](https://kobl.one/blog/create-full-ethereum-keypair-and-address/)
- [How are ethereum addresses generated?](https://ethereum.stackexchange.com/questions/3542/how-are-ethereum-addresses-generated)


The following is the sample code to create an address and a pair of private/public key.

```javascript=
const Wallet = require('ethereumjs-wallet');
const keccak256 = require('js-sha3').keccak256;

// keypair
const wallet = Wallet.generate();
 
// privKey
const privKey = wallet.getPrivateKey();
console.log("privKey:", privKey);
 
// pubKey
const pubKey = wallet.getPublicKey();
console.log("pubKey:", pubKey);

// address
let address = wallet.getAddressString();
console.log("address:", address);
```

The output is like this:

```
$ node key.js

privKey: <Buffer c7 49 b3 89 eb c3 28 3f 2e 52 5f fe 46 93 70 ed 37 64 85 1a 24 81 6d 56 54 cd 9d 99 f2 c1 2e f6>
pubKey: <Buffer 30 92 f7 ed ac aa 49 e0 f1 74 ea 63 53 ce be 65 aa 3f 73 32 18 51 62 cc 00 2f 23 9b 35 86 58 83 d7 bc c6 fd 49 69 b8 80 45 91 32 fe 6d c1 9d fa 6d 64 ... >
address: 0x759c946e5306e7e6498f4286055a931fe7b08882
```


#### (30%) a. Can you print the private/public key with hex string representation? Please give us an example.

For example, the following is the example of the private/public keys in hex string format. 

```
privKey: 
ff1140aabc074af4b6d84b74a0b9ba8bc00c18ad239d2b44208dcf6973a890cf

pubKey: 7b77b92d1a55ef612b93c6ac02d013c82ecf164eb6e59e9d0a1313c3dd511c0d7c00a0a78aca1befb5c5b7a2487e942b1916560394abee519db6585c16bad9a3

account:
0x013e06a5bd9e5d12edcec119d5816c37caa8e3c8
```

#### (20%) b. In addition, if we don’t want to use the getAddressString() to get the address, how can we obtain the address by hashing the public key?

```javascript=
/***** address *****/

// step 2:  public_key_hash = Keccak-256(public_key)
Your code

// step 3:  address = ‘0x’ + last 20 bytes of public_key_hash
Your code

console.log("address:", address);

```

#### (30%) c. There is a file called Keystore that is used to encrypt the private key and save in a JSON file. Can you generate a Keystore with the password "nccu"? You can find the details about Keystore below.


```jsonld=
{"address":"c2d7cf95645d33006175b78989035c7c9061d3f9",
  "crypto":{
    "cipher":"aes-128-ctr",
    "ciphertext":"0f6d343b2a34fe571639235fc16250823c6fe3bc30525d98c41dfdf21a97aedb",
    "cipherparams":{
      "iv":"cabce7fb34e4881870a2419b93f6c796"
    },
    "kdf":"scrypt",
    "kdfparams":{
      "dklen":32,
      "n":262144,
      "p":1,
      "r":8,
      "salt":"1af9c4a44cf45fe6fb03dcc126fa56cb0f9e81463683dd6493fb4dc76edddd51"
    },
    "mac":"5cf4012fffd1fbe41b122386122350c3825a709619224961a16e908c2a366aa6"
  },
  "id":"eddd71dd-7ad6-4cd3-bc1a-11022f7db76c",
  "version":3
}
```

- [Accounts, Addresses, Public And Private Keys, And Tokens]( https://theethereum.wiki/w/index.php/Accounts,_Addresses,_Public_And_Private_Keys,_And_Tokens) 
- [科普 | 什么是以太坊私钥储存（Keystore）文件？](https://ethfans.org/posts/what-is-an-ethereum-keystore-file)
- [What is an Ethereum keystore file?](https://medium.com/@julien.maffre/what-is-an-ethereum-keystore-file-86c8c5917b97)



## Resources

- https://github.com/ethereum/go-ethereum/tree/master/crypto (Golang)
- https://github.com/vkobel/ethereum-generate-wallet (Python)
- https://github.com/ethereum/eth-account (Python)
- https://github.com/ethereumjs/ethereumjs-wallet (JavaScript)
- https://github.com/emn178/js-sha3 (JavaScript)
- https://github.com/pubkey/eth-crypto/blob/master/README.md (JavaScript)


## Bonus (總成績加分)

- What is HD Wallet, BIP32, BIP39 and BIP44? (+2%) 
- What is RFC 6979 for? (+2%)

> Write an article, specify detailed background and problem statement as well as the scheme on how to address the problem. And publish the article on the Medium or somewhere.

