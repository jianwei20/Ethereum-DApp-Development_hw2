# Homework 2

## 作業繳交
:warning: 注意
- Deadline: 11/28 (before 11:59pm)
- How to submit? Register an account on  https://github.com/ and push your code and the answer there. 
:::


## 作業環境

1. 安裝 Node.js

2.安裝compiler 下載0.4.25版本solc
```
npm install -g solc@0.4.25
```

3.compiler Smart Contract
```
solcjs -o ./contract --bin --abi Bank.sol
```

4.安裝web3.js
```
npm install web3
```

5.用Web3.js來部署合約

```
node deploy.js
```

6.把合約地址放到 address.txt
