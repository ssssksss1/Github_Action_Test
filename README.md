# 깃허브 액션을 이용하여 PUSH하였을 떄 클라우드 인스턴스에 SSH로 접속하여 폴더 생성하기

#### 순서
1. [yml 설정](#yml 설정)
2. [github secret 설정](#github secret 설정)

### yml 설정
|번호|설명|
|:---:|:---:|
|01|프로젝트에 .github/workflows/main.yml 파일 만들기|
|02|아래와 같이 코드 작성하기|
'''
name: remote ssh command <br/>
on: [push] <br/>
jobs: <br/>
&nbsp;build: <br/>
&nbsp;&nbsp;name: Build <br/>
&nbsp;&nbsp;runs-on: ubuntu-latest <br/>
&nbsp;&nbsp;steps: <br/>
&nbsp;&nbsp;&nbsp;- name: executing remote ssh commands using password <br/>
&nbsp;&nbsp;&nbsp;&nbsp;uses: appleboy/ssh-action@master <br/>
&nbsp;&nbsp;&nbsp;&nbsp;with: <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;host: ${{ secrets.HOST }} <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;username: ${{ secrets.USERNAME }} <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key: ${{ secrets.KEY }} <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port: ${{ secrets.PORT }} <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;script: | <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sudo mkdir /app <br/>       
'''
