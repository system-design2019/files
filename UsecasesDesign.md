## BCE用例设计

#### 信息管理

（1）[注册](https://system-design2019.github.io/files/uml/design1-1)：用户使用邮箱或手机号进行注册，同时需要填写验证码

（2）[登录](https://system-design2019.github.io/files/uml/design1-2)：用户使用注册的邮箱/手机号进行登录，同时需要填写验证码

#### 任务发布

（1）[发布问卷](https://system-design2019.github.io/files/uml/design1-3)：用户在发布问卷时需要编辑题目内容、设置问卷参数、支付押金

（2）[发布跑腿](https://system-design2019.github.io/files/uml/design1-4)：用户在发布跑腿时需要设置跑腿内容、支付押金

#### 任务接受

（1）[填写问卷](https://system-design2019.github.io/files/uml/design1-5)：用户需要根据发布者的要求填写问卷，继而获得收益

（2）[参与跑腿](https://system-design2019.github.io/files/uml/design1-6)：用户根据发布者的要求选择参与跑腿，并处于安全性的考虑支付相应押金，发布者结束任务后可以获得收益并接收退回的押金



### 扩展用例

#### 信息管理

（1）[验证码](https://system-design2019.github.io/files/uml/usecase2-1)：用户在登录和注册时均需要填写验证码进行人机验证

（2）[修改密码](https://system-design2019.github.io/files/uml/usecase2-2)：用户通过原始密码验证后进行新密码的修改

#### 任务发布/接受

（1）[支付押金](https://system-design2019.github.io/files/uml/usecase2-3)：用户在发布问卷、发布跑腿、参与跑腿时均需要支付押金

（2）[编辑问卷题目内容](https://system-design2019.github.io/files/uml/usecase2-4)：用户可以发布包含选择题、填空题两种题型的问卷，并对题目属性做出设定

（3）[关闭任务](https://system-design2019.github.io/files/uml/usecase2-5)：关闭任务包含任务结束后的收益结算

（4）[查看参与情况](https://system-design2019.github.io/files/uml/usecase2-6)：问卷发布者可以查看问卷填写列表以及答案，跑腿发布者可以查看跑腿参与者

#### 收益相关

（1）[虚拟币](https://system-design2019.github.io/files/uml/usecase2-7)：M币为平台发布任务使用的虚拟代币，1元/枚，支持用户的充值与提现

#### 其他

（1）[通知系统](https://system-design2019.github.io/files/uml/usecase2-8)：支持用户接受通知、发送通知、删除通知、以及标为已读/未读等操作

