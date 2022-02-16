# 깃허브 액션을 이용하여 PUSH하였을 떄 클라우드 인스턴스에 SSH로 접속하여 폴더 생성하기
## API Specification
​
### Table of Contents
​
#### Auth
1. [회원 가입](#회원가입)
2. [로그인](#로그인)
3. [이메일 중복 체크](#이메일-중복-체크)
3. [닉네임 중복 체크](#닉네임-중복-체크)
4. [비밀번호 변경하기](#비밀번호-변경하기)
5. [access 토큰 재발급 (회원 재접속/새로고침 시)](#access-토큰-재발급)
#### User
1. [회원 상세 조회](#회원-상세-조회)
2. [회원 정보 수정](#회원-정보-수정)
3. [회원 탈퇴](#회원-탈퇴)
#### Store
1. [맛집 리스트 조회](#맛집-리스트-조회)
2. [맛집 상세 조회](#맛집-상세-조회)
3. [맛집 추가](#맛집-추가)
4. [맛집 정보 수정](#맛집-정보-수정)
5. [맛집 삭제](#맛집-삭제)
#### Upload
사진 업로드 - 파라미터에 type> user, store
​
​
### Auth
#### 회원가입
|Method|Endpoint|
|:---:|:---:|
**<span style="color:orange">POST</span>**|`/auth/signup`|
<br>
​
**Request Header**
|Header|Required|description|
|:---:|:---:|:---:|
|Content-Type| ✅ |application/json|
<br>
​
**Request Body**
|Field|Required|Type|Description|
|:---:|:---:|:---:|:---|
|nickname|✅|String|소셜로그인한 계정일 경우 랜덤값으로 [root]@[임의의 해쉬값] 생성|
|email|✅|String|id@domain으로 이루어졌는지 확인한다|
|password|✅|String|8자 이상|
<br>
​
**Response Body**
​
**1. `200` OK**
|Field|Type|Description|
|:---:|:---:|:---|
|statusCode|number|200|
|msg|string|Sign up Success|
