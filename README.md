# WHMCS_Alipay
**本项目是为了维护该插件在WHMCS 6.X正常使用而设，欢迎大家Fork&提交代码&反馈Bug!**

**原版已经开源，原作者为** [Bendy](mailto:67052@qq.com)  

本插件支持三种模式：即时到账，担保交易，双功能收款

# 目前在原版上改动了什么?

1、WHMCS 6.X后`dbconnect.php`被`init.php`替代 这个得换 不然会出错

2、原版的付款按钮丑的掺不忍睹，我换了个自认为能看的支付按钮（当然我们欢迎更好看的支付按钮，有更好看的按钮请Pull request!）


# 安装
下载ZIP包，解压包上所有的文件，并全部上传到whmcs安装目录的 `/modules/gateways` 目录下

上传后.访问 `http://你的whmcs网站地址/modules/gateways/callback/alipaytest.php` 测试连通性

# 货币设置
本接口设计时,只支持RMB作为货币单位,所以.你在WHMCS一定要先设置正确...

具体设置位置是管理员后台的`CONFIGURATION` =>  `CURRENCIES`

这个货币设置可能新手不太明白...

我分二种情况说明

**1,只使用RMB一种货币**  那直接填一个就OK了...不用费心，直接到下一步.

**2,使用二种以上的货币** 那就要涉及**WHMCS的货币换算了**.

填表的几个英文解析如下

`Currency Code` (货币代码,请按照国际标准填写RMB或者USD等货币代码)

`Prefix`	      (货币代号...按照国际惯例填$或者￥)

`Suffix`	      (货币名称...代号..比如"RMB""USD"...我建议与Currency Code保持一致)

`Format`	      (金额格式...默认就OK了)

`Base Conv. Rate`	 (这个要注意,是转换比率.使用二种以上货币时要设置.先假定一个基本货币.比如RMB..那设置RMB时候.这里填1..而设置USD的时候.这里就填6.85)

`Update Pricing*`  (更新价格)


#启用接口

设置完货币后..就可以启用接口了.

具体设置位置是`CONFIGURATION` => `PAYMENT GATEWAYS`

先在支付接口列表中找到alipay并按activite激活

几个设置详细说明:

`Show on Order Form`	 (在订单中显示使用本支付接口..前提是你要设置好相应的货币转换及金额.这个具体意义是"需要以RMB支付的时候,使用这个支付接口在订单里面)

`Visible Name`	      (客户看到的支付接口名称)

`类型`                (支付宝签约的三种类型,分别是1/即时到帐  2/担保交易   3/双功能

`卖家支付宝帐户`	    (你用来收款的支付宝帐号)

`合作伙伴ID`	        (合作ID和安全码..都在支付宝签约商家后台中找到.....什么?你还未签约???找支付宝吧，个人签担保交易应该很简单)

`安全检验码`	        （同上)

`Convert To For Processing`	  (如果你设置使用了二种或者二种以上的货币单位,必须转换货币...这里一定要有RMB.并选择RMB..否则支付接口不可用)

# 测试

设置完成后，你可以让别人用自己的支付宝来测试一下本插件是否正常工作

测试成功后就可以正常使用啦!

# Bug?贡献代码?
欢迎大家提交Bug和贡献代码!

我因为学业原因 暂时无力维护本项目
