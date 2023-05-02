# Solidity





## 一、入门

### 编译器

>使用在线编译器

地址:[Remix - Ethereum IDE](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.18+commit.87f61d96.js)





### 第一个程序

```solidity
ragma solidity ^0.4.16;

//创建一个结构
contract Helloword {
    string  Myname = "hyj";
    //函数标识
    function getName() public  view  returns (string memory)
    {
        return Myname;
    }

    function changeName(string name) public{
         Myname = name;
    }

    function pureTest(string name)pure  public  returns (string ) {
        return name;
    }
}  
```





