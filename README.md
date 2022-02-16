# 깃허브 액션을 이용하여 PUSH하였을 떄 클라우드 인스턴스에 SSH로 접속하여 폴더 생성하기

#### 순서
1. [yml 설정](#yml 설정)
2. [github secret 설정](#github secret 설정)
​
### Auth
#### 회원가입
|Method|Endpoint|
|:---:|:---:|
**<span style="color:orange">POST</span>**|`/auth/signup`|
<br>

**Request Header**
|Header|Required|description|
|:---:|:---:|:---:|
|Content-Type| ✅ |application/json|
<br>

**Request Body**
|Field|Required|Type|Description|
|:---:|:---:|:---:|:---|
|nickname|✅|String|소셜로그인한 계정일 경우 랜덤값으로 [root]@[임의의 해쉬값] 생성|
|email|✅|String|id@domain으로 이루어졌는지 확인한다|
|password|✅|String|8자 이상|
<br>

**Response Body**

**1. `200` OK**
|Field|Type|Description|
|:---:|:---:|:---|
|statusCode|number|200|
|msg|string|Sign up Success|
