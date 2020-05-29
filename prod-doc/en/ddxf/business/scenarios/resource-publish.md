# Resource publish

RP 将资源发布到某个 MP，等待 RC 购买。发布的内容包括资源的 DID/DDO 信息、元信息、待转移的权利、定价策略以及某个或某几个三方认证中心对该资源的认证信息(如果该资源有)等。MP将资源元信息等存入本地数据库，并做检索优化。MP 也将从链上取得相关交易历史信息和认证信息等进行展示。

用户和资源在历史交易中所得的评价将在一定的分布式声誉体系下转换成相应的评价分数，该评价得分会影响用户或资源在交易市场上的排名，进而会影响交易成交的可能性。

存在多个 MP，比如医疗数据交易市场，古董拍卖交易市场。每个交易市场接受不同类型的资源发布，同一资源也可以发布到不同的交易市场。





#### 数据通证交易、交换方式确定

1. [生成token，实现数据通证化](../../framework/data-storage/restful-api)
   
   * eshop 模式
     * DToken 的初始持有者即为 RC，随后该 DToken 可被(签发交易)流转给其他人。RP 在 DToken 时可以生成设定其流转次数限制，每次流转时该次数递减，流转次数为 0 即表示不可流转。
  * 在资源正式上传之前，为生成Token提供基本字段和数据，比如生成Token数量、资源权利的有限期等，通过 marketplace 提供的 SDK 调用 DToken 合约 ，而后生成具体的Token，实现人、财、物的绑定，方可进行签发交易流转流程。
   
   * data 模式
     * 资源上传时，RP 需要把生成 Token 的参数一起补充完整后上传，而后 RC 在执行购买操作时，通过 marketplace 提供时 SDK 的方法调用 DToken 合约及 MP 购买合约
   
2. 交换方式

   marketplace 提供了数据链上查询的 SDK ，平台方需要融合进自己的项目之中，能够让用户查看到数据的描述信息，平台方可自定义交换方式，比如线上或线下交易Token。

#### 链外数据纠纷的电子合同仲裁方案

1. RC 执行购买操作之后既可拥有该 Token 的所有权限，当 RC 申请仲裁时，MP 仲裁合约会质押此 Token ， 当 OJ 判定 RP 没有提供资源并将此结果输入交易的智能合约时，智能合约将做相应处理。

----



[Token 规范](../../framework/spec/data-token.md)


