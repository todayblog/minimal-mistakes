---  
layout: single  
title:  "git clone error - fatal early EOF fatal index-pack failed"  
tag: [git, clone, error, rpc, failed, curl, early, eof, fetch-pack]  
category:
  - git
  - github
  
toc: true  
toc_label: "My Table of Contents"  
toc_icon: "cog"  
---    
  
## Document Information  
- docNo: 20230125-1413  
- tag: #git #clone #error #rpc #failed #curl #early #eof #fetch-pack  
  
## Contents  
  
아래의 명렁어로 성공함  
stackoverflow 에서 검색된 여러가지 방법 다해보고 안되었는데 아래 명령어로는 성공했습니다.   
  
물론 ssh 로 clone 받기 위해서는 ssh key 설정이 되어 있어야 합니다.   
github 페이지에서 ssh key 설정하는 방법을 자세히 설명되어 있습니다.   
  
```bash  
git clone ssh://git@github.com:Cheolsoo/suby.git  
```  
  
  
## 참조  
[https://www.lesstif.com/gitbook/git-clone-fatal-early-eof-fatal-index-pack-failed-95879326.html](https://www.lesstif.com/gitbook/git-clone-fatal-early-eof-fatal-index-pack-failed-95879326.html)  
[https://stackoverflow.com/questions/21277806/fatal-early-eof-fatal-index-pack-failed](https://stackoverflow.com/questions/21277806/fatal-early-eof-fatal-index-pack-faile)  
  
