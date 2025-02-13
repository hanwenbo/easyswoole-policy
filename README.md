# EasySwoole Policy
用于验证、解析Policy结构和语法
## 安装
```bash
composer require EasySwoole/Policy
```
## 使用方法
```php

$policyData = [
	"Statement" => [
		[
			"Effect" => "Allow",
			"Action" => ["goods/*", "goods/list"],
		],
		[
			"Effect" => "Allow",
			"Action" => ["goods/*", "goods/list"],
		],
		[
			"Effect" => "Allow",
			"Action" => ["goods/*", "goods/list"],
		],
	],
];
$policy = new \EasySwoole\Policy\Policy();
$policy->addPolicy( new \EasySwoole\Policy\RequestBean\Policy( $policyData ) );
// 可以添加多组，目的：一个用户属于多个角色组的时候，或者一个角色组对应多个存储的policy的时候
$policy->addPolicy( new \EasySwoole\Policy\RequestBean\Policy( $policyData ) );
$result = $policy->verify( 'goods/list' );
var_dump( $result );
```


策略json格式如下：
```json
{
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "goods/*",
        "goods/list"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "goods/*",
        "goods/list"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "goods/*",
        "goods/list"
      ]
    }
  ]
}

```

- 前端policy验证的库 https://github.com/hanwenbo/policy.js
