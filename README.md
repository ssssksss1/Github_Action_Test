# 깃허브 액션을 이용하여 PUSH하였을 떄 클라우드 인스턴스에 SSH로 접속하여 폴더 생성하기

#### 순서
1. [yml 설정](#yml 설정)
2. [github secret 설정](#github secret 설정)

### yml 설정
|번호|설명|
|:---:|:---:|
|01|프로젝트에 .github/workflows/main.yml 파일 만들기|
|02|아래와 같이 코드 작성하기|
|
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
|

