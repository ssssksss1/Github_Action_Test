# 깃허브 액션을 이용하여 PUSH하였을 떄 클라우드 인스턴스에 SSH로 접속하여 폴더 생성하기

#### 순서
1. [yml 설정](#yml-setting)
2. [github secret 설정](#github-secret-setting)

---

#### Yml Setting
|번호|설명|
|:---:|:---:|
|01|프로젝트에 .github/workflows/main.yml 파일 만들기|
|02|아래와 같이 코드 작성해서 넣기

```
name: remote ssh command
on: [push]
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - name: executing remote ssh commands using password
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.HOST }}
          username: ${{ secrets.USERNAME }}
          key: ${{ secrets.KEY }}
          port: ${{ secrets.PORT }}
          script: |
            sudo mkdir /app      
```
---
#### Github Secret Setting
|번호|설명|
|:---:|:---:|
|01|프로젝트 저장소 - Settings - Secrets - Actions - New repository secret|
|02|Name : HOST , Value : 공인IP주소|
|03|Name : USERNAME , Value : opc 혹은 ubuntu 혹은 본인이 설정해놓은 인스턴스 사용자명|
|04|Name : KEY , Value : .ppk 파일에 내용을 넣으면 되는데 -----BEGIN RSA PRIVATE KEY----- ~ -----END RSA PRIVATE KEY----- 까지 전부 복사해서 넣어주어야 한다.|
|05|Name : PORT , Value : 22 (ssh 포트가 다르다면 알아서 바꾸기)|

---
