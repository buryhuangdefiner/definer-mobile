# definer-mobile

## 登录

### 注册一
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

### 注册二
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

### 注册三
建立密码
```
POST https://cognito-idp.us-east-1.amazonaws.com/
```
