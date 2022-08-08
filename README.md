# 代币合约

- 部分功能介绍：
  - 买卖滑点百分之5.5，在代币合约中，程序会扣手续费百分之5代币，市场管理扣百分之0.5代币，全部留存在当前合约的代币余额中。在分红时分手续费，自动转化为usdt。
  - 开始后一分钟，机器人扣手续费百分之90代币，转入指定账户。
  - 分红时会自动转换为usdt至合约账户，分红的usdt也由合约账户按分红比例转账至各分红用户。
  - 黑名单不能进行任何操作，合约部署黑名单，部署后可手动添加去除，但如果是分红用户目前可被分红。
  - 必须在博饼添加交易对。



# 环境信息

```
COMPILER: v0.8.7+commit.e28d00a7.js
Enable optimization: 开启并使用默认值200
Other Settings: default evmVersion, MIT license
```


# 操作流程

![image](https://user-images.githubusercontent.com/22724090/183380138-81a15619-7e89-42c0-b38d-da8d223fa280.png)

