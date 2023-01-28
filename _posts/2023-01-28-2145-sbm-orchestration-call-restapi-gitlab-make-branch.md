---
title: "gitlab 에서 branch 생성을 하는 curl 명령어를 sbm orchestration 으로 구현합니다."
tag: [sbm, orchestration, restapi, api ,token, gitlab, make, branch, gitlab-make-branch]
category: [sbm, gitlab, sbm-orchestration, gitlab-restapi, restapi]
layout: single
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
---

## Document Information
- docNo: 20230119-1644
- search: sbm orchestration restapi api token gitlab gitlab-make-branch sbm-orchestration

## Contents

아래 그림에서는 authorizationType 의 Default value 값이 공란 입니다.   
이런 경우 아래의 curl 명령어와 동일하게 브랜치가 생성되는지 테스트 합니다. 

### branch 생성 curl 명령어

```shell
curl --request POST --header "PRIVATE-TOKEN:glpat-yp2P_w3XeY6A5FwP8vn" "http://10.0.0.20:8001/api/v4/projects/2/repository/branches?branch=newbranch&ref=master"
```

### sbm orchestration RESTCaller_post 화면

![](/assets/attachments/Pasted%20image%2020230119164642.png)

훔 잘되네요, 원래 아래의 화면으로 테스트를 진행했었고 정상적으로 branch 가 생성 되었습니다. 

![](/assets/attachments/Pasted%20image%2020230119164903.png)

<font style="color:#ff0e0e">아마도 authorizationType 값이 SBMTOKEN 인것과 그냥 공란인 것은 차이가 없어 보입니다.</font><br>
<font style="color:#2f477a">아마도 authorizationType 값이 SBMTOKEN 인것과 그냥 공란인 것은 차이가 없어 보입니다.</font><br>

