На GitHub делаем Fork репозитория https://github.com/Kotlin-Polytech/KotlinAsFirst2020
Создаем копию репозитория с GitHub 
$ git clone git@github.com:AlinaSau/KotlinAsFirst2020.git
$ git clone git@github.com:AlinaSau/KotlinAsFirst2021.git
Затем прописываем команду для перехода в папку KotlinASFirst2020
$ cd KotlinASFirst2020
Указываем в качестве апстрима upstream-my свой форк KotlinASFirst2021
$ git remote add upstream-my https://github.com/AlinaSau/KotlinAsFirst2021
$ git fetch upstream-my
$ git merge upstream-my/master 
$ git push origin master
Проверяем все ли выполнилось с помощью команды
$ git remote -v 
Затем создаем ветку backport, возвращаемся на ветку master и переносим на backport коммиты 2021 года 
$ git checkout -b backport
$ git checkout master
$ git rebase backport
Создаем апстрим upstream-theirs с форком одногруппника
$ git remote add upstream-theirs https://github.com/AleksKen/KotlinAsFirst2021
$ git fetch  upstream-theirs
$ git merge  upstream-theirs
Проверяем все ли выполнилось с помощью команды
$ git remote -v 
Создаем новую ветку, в которую поместим репозиторий одногруппника
$ git checkout -b Maria
Переносим коммиты одногруппника на созданную ветку, устраняя конфликты
$ git config merge.tool vimdiff
$ git config merge.conflictstyle diff3
$ git config mergetool.prompt false
$ git mergetool
$ git cherry-pick 841211facf9a7538a1a3077eec50c42af507cdb8
$ git mergetool
$ git cherry-pick –continue
Проверяем все ли выполнилось с помощью команды
$ git remote -vv
Переключаемся на ветку мастер и добавляем в нее ветку с репозиторием одногруппника
$ git checkout master
$ git merge Maria
Создаем текстовый документ remotes, в который записываем вывод remote -v, и коммитим его
$ touch remotes.txt
$ git add remotes.txt
$ git commit -m 'текст'