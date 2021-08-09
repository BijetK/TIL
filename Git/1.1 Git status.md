```bash
$ git status

On branch master

# 커밋이 될 변경사항들
# staging area에 있는.. staged 상태의 파일들..
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    b.txt
        
# staged(commit을 위한) 아닌 변경사항들
# Working Directory에 있는.. 수정된 파일들 (기존에 커밋된 적 있는 파일)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt
        
# 트래킹 X 파일들
# 커밋이 된적 없는 파일들..
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.docx
```

