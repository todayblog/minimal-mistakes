---      
title:  "백업 디렉터리에서 최근 3개만 남기고 나머지 삭제하는 스크립트"
tag: [shell-script, shell, script, backup, directory, folder, delete, delete-backup-directory, 백업, 디렉터리, 삭제]
category:
    - shell-script
layout: single
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
---

## Document Information  
- docNo: 20230125-1708  
- tag: #shell-script #shell #script #backup  #directory #folder #delete #directory #delete-backup-directory  
  
## Contents  
  
```bash  
fn_deleteBackup() {  
    local backupDir=$1  
    cnt=`ls ${backupDir} | wc -l`  
  
	if [ $cnt -lt 3 ]; then  
		return 0  
	fi  
  
	cntLimit=`expr $cnt - 2`  
	cntDel=0  
  
	while read line  
	do  
		cntDel=`expr $cntDel + 1`  
		if [ $cntDel -gt $cntLimit ]; then  
			break  
		fi  
		  
		echo "# ::: 오래된 백업 디렉터리 삭제"  
		echo "# ::: rm -fr ${backupDir}/${line}"  
		rm -fr "${backupDir}/${line}"  
	done < <(ls ${backupDir} | sort)  
}  
```  
