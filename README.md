# 代币合约

- 部分功能介绍：
  - 普通账户用户在交易所买卖滑点百分之5.5，在代币合约中，程序会扣手续费百分之5代币，市场管理扣百分之0.5代币，全部留存在当前合约的代币余额中。在分红时分手续费，自动转化为usdt。
  - 开始后一分钟，机器人扣手续费百分之90代币，转入指定账户。
  - 分红时会自动转换为usdt至合约账户，分红的usdt也由合约账户按分红比例转账至各分红用户。
  - 黑名单不能进行任何操作，合约部署黑名单，部署后可手动添加去除，但如果是分红用户目前可被分红。
  - 白名单在执行任何操作时都不会扣手续费，合约开始前可以转账代币，添加流动性。
  - 普通用户只有开始后可进行用户之间直接转账（不扣手续费），交易所买卖（手续费），添加流动性（不扣手续费）。
  - 必须在博饼添加流动性，账户添加流动性后即可参与分红。



# 环境信息

```
COMPILER: v0.8.7+commit.e28d00a7.js
Enable optimization: 开启并使用默认值200
Other Settings: default evmVersion, MIT license
```


# 操作流程

编译：

注意合约名和文件名保持一致，注意红色框，和编译的文件（未在图中出现，但在remix中下拉即可看到，注意选择被编译的文件），点击编译按钮。

![image](https://user-images.githubusercontent.com/22724090/183380138-81a15619-7e89-42c0-b38d-da8d223fa280.png)

部署：

注意选择测试环境，部署按钮Deploy后输入合约用户地址（在metaMask钱包客户端可以复制地址，输入的参数即为合约的tokenOwner，代币所有者地址，部署成功后会转账规定的代币数量到此账号。），选择正确的合约部署，注意红色框。

![image](https://user-images.githubusercontent.com/22724090/183381629-0085a33f-0492-409f-bd55-2e542540c655.png)

使用：
部署成功后，会自动得到下图的合约，红色框中包含地址，复制地址以备后续流程使用，如果刷新页面在Ataddress按钮后输入地址可重新载入合约。（remix规定，只有合约部署人的账户有此权限，并且不灵时多刷新几次页面。）
![image](https://user-images.githubusercontent.com/22724090/183559760-0641e2fa-4c10-4133-9767-1c1e65497a9c.png)

操作第一步：

tokenOwner添加流动性：

首先登陆pancake，使用tokenOwner登录，测试环境使用WBNB（用测试环境BNB兑换。）和当前合约的Token（通过上一步复制的合约地址搜索。）来添加流动性，注意红色框。

![image](https://user-images.githubusercontent.com/22724090/183578261-7c2633df-c96f-4a4d-bddd-28f22693290b.png)

完成添加流动性可以看到下图中红色框中的内容：

![image](https://user-images.githubusercontent.com/22724090/183579288-d6230dc6-21a8-4f64-9155-92fc7b93d793.png)

添加完成交易记录图：

![image](https://user-images.githubusercontent.com/22724090/183583967-8b05527d-2b3e-49f7-adc9-eaa078992691.png)



操作第二步：

开始合约，在下图1红色框选项中填入数组0，点击按钮即可开始合约。如在此之前需要添加白名单，在下图2中添加，过后随时都可以进行前述的开始操作。（白名单人员可在开始前添加流动性等操作。）

图1：

![image](https://user-images.githubusercontent.com/22724090/183579830-54195332-b9ab-4c94-af24-7fd158aa9a1c.png)

图2：

![image](https://user-images.githubusercontent.com/22724090/183580386-e274a204-e8c8-4b9f-ba13-586fc8b28f0a.png)


操作第三步：

普通用户和白名单用户都可以在pancake交易（如下图1，2），添加流动性（如下图3），除合约持有者外卖出和添加流动性都可以触发分红操作，（有金额等其他相关的触发条件，核心还是达到一定的可分红金额累计，也是最低的可允许分红的金额限制，综合考虑，这里不详述兑换和分红算法。）注意红色框。

图1：

![image](https://user-images.githubusercontent.com/22724090/183581165-06e2c0b6-f962-4ae2-b62f-9f75bdd449e1.png)

图2：

![image](https://user-images.githubusercontent.com/22724090/183582533-3e2c0183-34db-4fff-9844-ca55c3a2c653.png)

图3：

![image](https://user-images.githubusercontent.com/22724090/183582777-10aac5b7-c3f7-4e75-b3d5-67d1ebc8bc08.png)

上述的交易记录图：

买入：

![image](https://user-images.githubusercontent.com/22724090/183584634-5abb7663-c1f1-4e54-a9f2-8cb2d8914ccb.png)

卖出（红色框为本次卖出的路由和费用）：

![image](https://user-images.githubusercontent.com/22724090/183584777-d2ca1033-dfec-45ff-885c-724212b08d44.png)

分红记录（红色框为随本次卖出的分红记录）：

![image](https://user-images.githubusercontent.com/22724090/183585066-b52f9d53-6b38-4b1a-aaca-6f7afa32ebec.png)

注意：分红的算法在代码中直接阅读即可，或者联系开发人员，分红的手续费为触发用户花费。（一定意义上的随机，因为每次触发分红需要花费额外转账的gas费，所以每次分红限制25人目前。）

# 结束。
