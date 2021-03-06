## 电商后台

在电商企业中，后台系统主要的作用是业务支撑、优化服务流程、提高服务效率，还可以提供数据分析参考，进而为业务调整提供参考。

产品架构与技术架构相辅相成，产品架构决定需求和设计，技术架构决定技术框架与性能。

## 产品模块
（1）商品中心：主要管理SKU（最小库存单位）、SPU（标准化产品单元）、属性（关键属性、非关键属性、销售属性）、类目品牌、价格等有关商品的数据。

（2）订单中心：管理订单类型、订单状态，收集关于商品、优惠、用户、收货信息、支付信息等一系列的订单实时数据，进行库存更新、订单下发等一系列动作。

（3）支付中心：管理支付数据，调用第三方支付平台接口，记录支付信息（对应订单号、支付金额等），支付对账。

（4）会员中心：主要管理用户等级、用户权益、积分、卡券等会员相关信息，通过一系列满足用户心理、提高黏性的方法来实现开发新用户、增加用户活跃度的目的。

（5）调度中心：将订单信息转化为发货通知单，以及其他出入库单，调度仓库和物流进行发货。

（6）促销中心：主要管理活动相关，优惠券、满减、专场活动、促销专区等。促销工具的开发对电商尤其重要。促销活动的滥用易造成的用户疲劳，怎样推陈出新，给产品经理造成了很大挑战。

（7）内容管理系统：主要是对用户端进行页面配置（Banner、ICON、Tab），配置首页，自定义活动页面，设置生效时效。

（8）评价中心：管理商品评价和用户反馈。这并没有想象的那么简单，涉及一些敏感词和敏感图片的筛选，以及回复内容管理。

（9）采购中心：管理SKU，当库存预警时，及时生成采购单进行入库。有供应商管理模块，主要进行供应商管理评级，发展新供应商等功能。

（10）财务管理：主要管理订单、采购系统相关的财务数据，数据准确性要求较高。还需要负责对账、清账、统计等业务。

（11）WMS系统（仓库管理系统）：主要包括入库、出库、盘点等模块。WMS主要和调度中心进行数据交互，反馈出入库状态和库存变动。

（12）物流中心：主要包括运费模板，负责运费管理（前端订单、真实物流成本）、物流状态保存查询（包括快递100、菜鸟等关联业务）。如果是跨境电商，还涉及和海关总署的对接，进行报关操作。

（13）风控中心：主要利用大数据进行用户信用建设、反欺诈，避免恶意评价、刷单退款等操作，构建安全的电商购物环境。

（14）客服中心：主要管理退货退款、售后服务等操作，包括呼叫中心、在线客服等，与之对应的是工单系统，将客服任务进行队列管理，分配给相应的客服。

（15）店铺管理：功能庞杂，相当于提供给B端用户一个Saas管理后台，提供管理商品、营销、订单一系列功能，主要针对一些有对B端业务的电商开放平台。

## 参考

摘于电商产品经理宝典

