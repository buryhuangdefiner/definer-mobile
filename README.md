# definer-mobile

## 登录
### 已有账号
```
POST https://cognito-idp.us-east-1.amazonaws.com/
{
	"AuthFlow": "USER_SRP_AUTH",
	"ClientId": "68qp95bbpg5r41f02i9bg75s0u",
	"AuthParameters": {
		"USERNAME": "tester@gmail.com",
		"SRP_A": "6636675ef7e3643c05cd7c87a536aa48b546257cca4bad167746a1c19dad9c8c70df58c65442f2a4e90d4359c40ea71850294c8d006c5ad53141c06527b327b3b8f07a43b6ae119d3da71b0e4f37a4f2340bc5ff629142039ba2e6772b1f36a998acb2b9ed9f5137a282f09129c9212ddb704495797ef1b2a4721d54445e57ddb47ef5d201f29d8057ca1ada63aa1937c7933aa8155ea08bf617cea328a829891882b1fdf65b84946bb6ad5c622a2c8f3e8c5078b6f4cfbc7c20f8a17d8ef6587d243079540c70ea9d3fa9be91102425b175a73dedf68e33e932160b12039c8b3429412cb276d0de6c9dd8ccf580f9478d416e1781851f1267d4fb486019044b46ef016712e101df927f2d0f0f2ea057bf0da894b89728449550aee237909db94a64390372f4e4f7ca2a00e330e5778aee2c41f71ac53a3af4628b6c03a3b453115becaa09ce406b49740883fb788d87a1aaa09256d3426e50a87806f373156c2b0eb905dd9f43716433a756012e0ea11d8a7e873eb248289d40937b6c01c34f"
	},
	"ClientMetadata": {}
}
```
### 新建账号
#### 注册一
生成账号地址
abc@gmail.com => a300576e-f342-5326-990d-629080ea930f

检查邮箱地址
GET https://api.definer.org/<API_KEY>/definer/api/v1.0/accounts/<账号地址>

发送验证邮件
```
POST https://api.definer.org/<API_KEY>/definer/api/v1.0/accounts/<账号地址>
{
	"accountId": "a300576e-f342-5326-990d-629080ea930f",
	"data": {
		"accountid": "a300576e-f342-5326-990d-629080ea930f",
		"email": "haohua.huang@gmail.com"
	},
	"status": "VALIDATION_EMAIL_SENT"
}
```

#### 注册二
无API, App循环检测邮件是否已验证
检查邮箱地址
```
GET https://api.definer.org/<API_KEY>/definer/api/v1.0/accounts/<账号地址>
{
	"accountId": "a300576e-f342-5326-990d-629080ea930f",
	"data": {
		"accountid": "a300576e-f342-5326-990d-629080ea930f",
		"email": "haohua.huang@gmail.com"
	},
	"status": "VALIDATION_EMAIL_SENT"
}
```

#### 注册三
建立密码
```
POST https://cognito-idp.us-east-1.amazonaws.com/
```
