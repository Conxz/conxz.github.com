Source files for my personal hexo [blog](http://www.conxz.net).

####History:

#####1-Mar-2017 add backup for themes folders
git ls-files --stage | grep 160000

git rm --cached maupassant

git add maupassant

git commit -m 'add bakup for themes'

git push

#####22-Feb-2017 new branch 'hexo' for source files backup.
git remote

git remote add origin https://github.com/Conxz/conxz.github.com.git

git remote

git push -u origin HEAD:hexo

git checkout hexo

git push

touch README

git add README

git commit -m 'init README'

git push 

git mv README README.md

git commit -m 'rename README'

git push


Other helpful cmds:

git status

git remote rm origin
