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
		"email": "tester@gmail.com"
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

## 借出/借入
### 主列表
```
GET https://api.definer.org/<API_KEY>/definer/api/v1.0/contracts
{
	"data": [{
		"contractId": "c8d7dc420aa14061ac1878ad5a92af65",
		"create_time": "2019-12-28 15:23:22",
		"create_timestamp": 1577546602.797457,
		"data": {
			"0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee": 1,
			"apr": 10,
			"borrowAmount": 2,
			"borrowerAddr": "0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee",
			"collateralAmount": 3.0303,
			"collateralApproved": 0,
			"contractType": "T2T",
			"createdByAddr": "0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee",
			"currentState": 0,
			"currentUser": "0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee",
			"daysPerInstallment": 30,
			"fundAddr": "0x89d24a6b4ccb1b6faa2625fe562bdd9a23260359",
			"fundLabel": "DAI",
			"installmentPay": 2.016667,
			"installmentsLeft": 1,
			"lenderAccountId": "4f556122-3884-586e-b15f-d765cd5eb7d4",
			"loanId": "c8d7dc420aa14061ac1878ad5a92af65",
			"loanType": "Borrower Initiated",
			"name": "buryhuan: Borrow 2 DAI @ 10% for 30 Days",
			"numberInstallments": 1,
			"ownerAddr": "0x095869e1893eed9a2ca3925e3edd25eb0dccb6f5",
			"paybackAmount": 2.016667,
			"startTime": 1577546602.797457,
			"timeBetweenInstallments": 30,
			"tokenAddr": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
			"tokenLabel": "USDC",
			"totalLoanTerm": 30
		},
		"status": 0
	}, {
		"contractId": "ab33a004f3fe4c2587361cd3abd3e8cd",
		"create_time": "2019-12-24 02:45:17",
		"create_timestamp": 1577155517.90523,
		"data": {
			"0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee": 1,
			"apr": 5,
			"borrowAmount": 30,
			"borrowerAddr": "0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee",
			"collateralAmount": 5804.5455,
			"collateralApproved": 0,
			"contractType": "T2E",
			"createdByAddr": "0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee",
			"currentState": 0,
			"currentUser": "0xc0d0759db45ae3cc3661d699fc67ca8accacc3ee",
			"daysPerInstallment": 30,
			"fundAddr": "0x000000000000000000000000000000000000000E",
			"fundLabel": "ETH",
			"installmentPay": 30.125,
			"installmentsLeft": 1,
			"lenderAccountId": "4f556122-3884-586e-b15f-d765cd5eb7d4",
			"loanId": "ab33a004f3fe4c2587361cd3abd3e8cd",
			"loanType": "Borrower Initiated",
			"name": "buryhuan: Borrow 30 ETH @ 5% for 30 Days",
			"numberInstallments": 1,
			"ownerAddr": "0x095869e1893eed9a2ca3925e3edd25eb0dccb6f5",
			"paybackAmount": 30.125,
			"startTime": 1577155517.90523,
			"timeBetweenInstallments": 30,
			"tokenAddr": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
			"tokenLabel": "USDC",
			"totalLoanTerm": 30
		},
		"status": 0
	}]
}
```

### 详情
合同ID: a1a785aea7524b3d83c3103c00cbb0e2
```
GET https://api.definer.org/OKh4I2yYpKU8S2af/definer/api/v1.0/contracts/<合同ID>
{
	"contractId": "a1a785aea7524b3d83c3103c00cbb0e2",
	"create_time": "2019-09-29 02:39:01",
	"create_timestamp": "1569724741.073059",
	"data": {
		"0x7bf939980228d01701a1f0e2f4b0d28fee33af1e": 1,
		"0xbe1e88fdcd1471a9472b78bb21c642e33977fec0": 1,
		"acceptedByAddr": "0x7bf939980228d01701a1f0e2f4b0d28fee33af1e",
		"apr": "9.001000",
		"borrowAmount": 640,
		"borrowerAddr": "0x7bf939980228d01701a1f0e2f4b0d28fee33af1e",
		"canAccept": 1,
		"canCounter": 1,
		"canModify": 0,
		"collateralAmount": "7.390000",
		"createdByAddr": "0xbe1e88fdcd1471a9472b78bb21c642e33977fec0",
		"currentState": 0,
		"currentUser": "0x7bf939980228d01701a1f0e2f4b0d28fee33af1e",
		"date": "9/28",
		"daysPerInstallment": 365,
		"fundAddr": "0x89d24a6b4ccb1b6faa2625fe562bdd9a23260359",
		"inProgress": 1,
		"installmentPay": "698.406489",
		"installmentsLeft": 1,
		"lenderAddr": "0xbe1e88fdcd1471a9472b78bb21c642e33977fec0",
		"loanAmount": 640,
		"loanId": "a1a785aea7524b3d83c3103c00cbb0e2",
		"loanType": "Lender Initiated",
		"name": "Fergus Oct.",
		"paybackAmount": "698.406489",
		"premium": "58.406500",
		"startTime": "1569724741.073059",
		"status": "Proposing",
		"tokenAddr": "0x000000000000000000000000000000000000000E",
		"tokenLabel": "ETH",
		"totalLoanTerm": 365
	},
	"status": 0
}
```
