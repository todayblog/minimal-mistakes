---
title: "root 계정이 아닌 일반 계정으로 docker 실행하는 방법"
tag: [docker, root, 권한, 일반계정, 일반, 계정, 실행]
layout: single
category: [docker]
toc: true  
toc_label: "My Table of Contents"  
toc_icon: "cog"  
---  
  
# Document Information  
- docNo: 20230118-1431  
- tag: #docker #root #권한 #일반계정 #일반 #계정 #실행   
  
# Contents  
  
root 계정이 아닌 일반 계정으로 실행하면 아래와 같은 에러가 발생함  
  
```bash  
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create: dial unix /var/run/docker.sock: connect: permission denied.  
```  
  
이를 해결하기 위한 방법중 하나로  
  
1. docker 그룹 생성  
2. 일반 사용자를 docker 그룹에 추가  
  
## cskim 계정의 그룹 확인 및 추가   
  
여기서는 일반계정을 cskim 으로 가정하고 진행합니다.   
만일 본인이 사용하는 계정이 chris 라고 한다면 cskim 대신 chris 를 사용하시면 됩니다.   
  
```shell  
groups cskim  
```  
  
## docker 그룹 생성  
  
```shell  
sudo groupadd docker  
```  
  
cskim 사용자를 docker 그룹에 추가한다.   
  
```shell  
sudo usermod -aG docker cskim  
```  
  
<font style="color:#f1c40f">그룹 추가후 cskim 계정은 로그아웃 했다가 다시 로그인 해야 합니다. </font>   
  
## docker 소켓 파일 그룹과 권한 설정  
  
만일 위의 작업들을 수행해도 오류가 발생한다면 아래의 방법을 진행합니다.   
  
### 소켓 파일 그룹 지정  
  
```shell  
sudo chown root:docker /var/run/docker.sock  
```  
  
### 소켓 파일 실행 권한 변경  
  
```shell  
sudo chmod 666 /var/run/docker.sock  
```  
  
### 유효성 검사  
  
`sudo` 권한 없이 `docker` 명령어를 사용할 수 있는지 테스트  
  
```shell  
docker run --rm hello-world  
```  
  
### 비슷하지만 다른 에러  
  
디렉터리 권한 문제일 수도 있다.   
  
```  
WARNING: Error loading config file: /home/user/.docker/config.json -stat /home/user/.docker/config.json: permission denied  
```  
  
## 모든 docker 프로세스 죽이기  
  
tag: #docker #ps #kill   
  
```shell  
docker kill -f $(docker ps -a -q)  
```  
  
