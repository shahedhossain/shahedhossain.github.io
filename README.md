# [shahed-site-ngular][201]

This is an angular client application to support fontend Symfony projects of [`Chorke, Inc.`][000]. Any Composer based php project can access this project and it's dependencies as following:


### require config for `composer.json`

```json
{
    "require": {
        "shahed/shahed-site-ngular": "1.0.*"
    }
}
```


This is an confidential resource and library of [Chorke, Inc.][000] unauthorized usage not permitted. Only the authorized person can be clone this project using Git Source Control Manager:

1. [`git clone bit.chorke.org:shahedbiz/shahed-site-ngular.git`][201] from [bit://shahedbiz][200]
2. [`git clone git.chorke.org:shahedbiz/shahed-site-ngular.git`][301] from [git://shahedbiz][300]


### upload `rsa` keys then add to `~/.ssh/config`

```cfg
Host bit.chorke.org
     HostName bitbucket.org
     PreferredAuthentications publickey
     IdentityFile ~/.ssh/bit_chorke_rsa
     User git
    
Host git.chorke.org
     HostName github.com
     PreferredAuthentications publickey
     IdentityFile ~/.ssh/git_chorke_rsa
     User git
     
```


### build multiple modules by shell

```bash
\
a='static strict ngular webapp';\
printf "\n\033[0;33mDo you wish to:\033[0m\n";select o in 'update' 'install' \
'phpunit';do case $o in 'install') break;; 'update') break;; 'phpunit') break\
;;esac;done;f="composer %s --prefer-dist";printf -v c "$f" "$o";printf \
"\nYour option is: \033[0;35m%s\033[0m\n" "$o";if [ "$o" == "update" ];then \
o="$(echo $o|perl -ne 'print substr($_,0,5)')";fi;if [ "$o" == "phpunit" ];\
then o='test';fi;for m in $a;do d="shahed-site-$m";c='';\
if [ "$o" == "install" ]||[ "$o" == "updat" ];then \
f="composer %s --prefer-dist";printf -v c "$f" "$o";\
if [ -d $d ]&&[ -f "$d/composer.json" ];then cd $d;\
printf '\n%sing \033[0;35m%s\033[0m\n' "$o" "$d";$c;cd ..;fi;fi;\
if [ "$o" == "test" ];then if [ -f "$d/vendor/bin/simple-phpunit" ];\
then c='./vendor/bin/simple-phpunit';else c='./vendor/bin/phpunit';fi;\
if [ -d $d ];then cd $d;printf '\n%sing \033[0;35m%s\033[0m\n' "$o" "$d";\
$c;cd ..;fi;fi;done

```


### push multiple modules by shell

```bash
\
a='static strict ngular webapp';\
u="$(git config user.name)";for s in $a;do m="shahed-site-$s";d="./$m";\
if [ -d $d ]&&[ -d "$d/.git" ];then f='%s by %s on %s';\
t="$(date +'%d%b%Y %R %p'|tr '[:lower:]' '[:upper:]')";cd $d;\
if [[ "$(git diff --cached --numstat|wc -l|tr -dc '0-9')" -gt '0' ]];\
then cd ..;printf '\npushing \033[0;32m%s\033[0m\n' "$m";\
select q in 'Yes' 'No';do case $q in 'Yes') break;; 'No') break;;esac;done;\
if [ "$q" == 'Yes' ];then printf '\nNotes for \033[0;32m%s\033[0m: ' "$m";\
read n;printf -v c "$f" "$n" "$u" "$t";cd $d;\
git commit -m "$c";git push origin master;cd ..;fi;else cd ..;\
printf '\n\033[0;31mNo index\033[0m \033[0;32m%s\033[0m\n' "$m";fi;fi;done

```


### pull multiple modules by shell

```bash
\
a='static strict ngular webapp';\
printf "\n\033[0;33mDo you wish to:\033[0m\n";select o in 'fetch' 'pull';\
do case $o in 'fetch') break;;'pull') break;;esac;done;for s in $a;\
do m="shahed-site-$s";d="./$m";if [ -d $d ]&&[ -d "$d/.git" ];then cd $d;\
if [[ $(git status --porcelain|wc -l|tr -dc '0-9') -eq '0' ]];then cd ..;\
printf '\n%sing \033[0;32m%s\033[0m\n' "$o" "$m";select q in 'Yes' 'No';\
do case $q in 'Yes') break;; 'No') break;;esac;done;\
cd $d;if [ "$q" == 'Yes' ];then if [ "$o" == "fetch" ];then \
git fetch --all;git fetch --tags;git pull origin master;\
else git pull origin master;fi;fi;cd ..;else cd ..;\
printf '\n\033[0;31mcommit/reset\033[0m \033[0;32m%s\033[0m\n' "$m";fi;fi;done

```


### good to know for composer opts

```bash
bin/console generate:bundle --namespace=Shahed/Bundle/NgularBundle \
--bundle-name=Bundle --format=annotation

ng build --prod --aot --output-hashing=none --vendor-chunk=false \
--build-optimizer  --base-href=/

composer require chorke/chorke-comn-utlity
composer config -g secure-http false
composer install --prefer-dist
composer update --prefer-dist
php bin/console server:start
composer update --no-scripts
self-update --rollback
composer self-update
composer clear-cache
ng serve

```


### good to know for git and shell

```bash
# good to know for delete commit
git reset --hard HEAD^
git push --force

# good to know for delete gittag
git push --delete origin tagname
git tag  --delete tagname

# good to know before git ignore
git rm --cached to/file/path/name.*
git rm --cached to/file/path/name.ext

# good to know git stop tracking
git update-index --assume-unchanged to/file/path/name.*
git update-index --assume-unchanged to/file/path/name.ext

# good to know for find and replace
for f in $(find ./app/ -name '*.php'); do sed "s/ebis/ehis/g" \
"$f"> "$f.tmp" && mv "$f.tmp" "$f"; done;

```


### repository config for `composer.json`

```json
{
  "repositories": [{
    "type": "composer",
    "name": "pkg.chorke.com",
    "url" : "http://pkg.chorke.com"
  }]
}
```


### http basic auth config for `~/.composer/auth.json`

```json
{
    "http-basic": {
        "pkg.chorke.com": {
            "username": "composer",
            "password": "chorkeinc"
        }
    }
}
```


### About the Project

Actually it's not a complete project, it's can be best defined as library. While this project started aim to build the foundation/skeleton of enterprise graded project. Base on this foundation/skeleton any one can able to build enterprise application. This library/foundation/skeleton project will reduce the learning curve and maximized the productivity.


### About [Chorke, Inc.][000]

[`Chorke, Inc.`][000] founded aimed to develop `Open Source Enterprise Graded Application`, based on `Java`, `JavaScript`, `Ruby`, `Python` and `PHP`. Integrated, Modularized, Simplified and loosely coupled application development is our vision. Our goal is minimize the learning curve, maximizing the productivity using `Open Source` technology. Trying the best practice to transparent and enrich software development using `OOP(Object Oriented Programming)`. Our development process accelerated by `XP (Extreme Programming)` and Agile Scrum Master. While it's reduce the time and costing.


### About Founder

**Md Shahed Hossain**, **Rashida Akter** is the co-founder of [`Chorke, Inc.`][000] and **Raiyan Bin Shahed** is the next successor. Mr. **Shahed** is an enthusiastic java developer and open source community leader. Mrs. **Rushi** is his lady and **Raiyan** is their elder son. Who are the part of inspiration, innovation and contribution to [`Chorke, Inc.`][001]


### Contact

- [**devs@chorke.com**][100]
- [**devs@chorke.org**][101]
- [**www.chorke.com**][000]
- [**www.chorke.org**][001]


[000]:  http://chorke.com "Chorke, Inc. Visit us"
[001]:  http://chorke.org "Chorke, Org. Visit us"

[100]:  mailto:devs@chorke.com "Chorke, Inc. Email us"
[101]:  mailto:devs@chorke.org "Chorke, Org. Email us"

[200]:  https://bitbucket.org/shahedbiz "bit://shahedbiz"
[201]:  https://bitbucket.org/shahedbiz/shahed-site-ngular "shahed-site-ngular"

[300]:  https://github.com/shahedbiz "git://shahedbiz"
[301]:  https://github.com/shahedbiz/shahed-site-ngular "shahed-site-ngular"
