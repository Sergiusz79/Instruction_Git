# Руководство пользователя

## Основные команды Git

1. **git –version** – отображает текущую установленную версию программы
2. **git init** – инициализация (указываем папку в которой git начнёт отслеживать изменения)
3. **git status** – показывает текущее состояние гита, есть ли изменения которые нужно сохранить (сделать commit)
4. **git add** - добавляет содержимое рабочего каталога в индекс (staging area) для последующего коммита. Эта команда дается после добавления файлов. Писать название целиком не обязательно: терминал дозаполнит данные автоматически.
5. **git commit** - зафиксировать или сохранить По умолчанию git commit использует лишь этот индекс, так что вы можете использовать git add для сборки слепка вашего следующего коммита. (команда git commit берёт все данные, добавленные в индекс с помощью git add, и сохраняет их слепок во внутренней базе данных, а затем сдвигает указатель текущей ветки на этот слепок)
6. **git log** - Журнал изменений (перед переключением версии файла в git используйте команду git log, чтобы увидеть количество сохранений). Эта команда показывает все сохранённые изменения от последнего к первому
7. **git checkout** - Переключение между версиями (откат в “прошлое”)
8. **git checkout master** - вернуться в главную ветку
9. **git diff** - Показывает разницу между текущим файлом и сохранённым (Перед переключением версии файла в Git используйте команду **git log**, чтобы увидеть количество сохранений)
10. **git reset HEAD^** - Эта команда перемещает текущую ветку назад на два коммита, эффективно удаляя два снапшота, которые мы только что создали, из истории проекта. Он отменяет случайное закоммичивание и сохраняет изменения
11. **git bisect** - Эта команда используется для обнаружения коммита, вызвавшего ошибку в коде. Так проще отследить коммит, где код работает и выявить проблемный коммит
12. **git stash** - Эта команда используется для сохранения неподтверждённых изменений в отдельном хранилище, чтобы можно было вернуться к ним позже. Сами  файлы возвращаются к исходному состоянию. Команда полезна, когда вы работаете над одной веткой, хотите переключиться на другую, но вы ещё не готовы сделать коммит в текущей ветке. Таким образом, вы прячете изменения в коде, переключаетесь на другую ветку, возвращаетесь к исходной ветке, а затем разархивируете свои изменения. Команда **git stash pop** -  позволяет применить ранее отложенные изменения

### _Примечания_

* Git отслеживает файлы по имени! Если изменить имя файла, то необходимо добавить файл с новым (изменённым) именем + git commit
* **Clear** – очищает окно терминала
* **Нажатие клавиши ‘q’** - возвращает в исходное окно терминала.
* **Чтобы вызвать** - ранее введённую команду, пользуемся стрелками на клавиатуре. Перебираем недавно введённые команды нажатием стрелки «вверх»
* **git clean -f** - Эта команда используется для удаления неотслеживаемых файлов из  вашего локального репозитория
* **git clean -d** - Эта команда используется для удаления неотслеживаемых директорий в вашем локальном репозитории. Вы также можете объединить его с **git clean -fd**, чтобы сделать и то, и другое.

## Работа с ветками

1. **git branch** – выводит список веток и показывает в какой ветке мы сейчас находимся
2. **git branch branch_name** – создание ветки с именем branch_name
3. **git branch -d branch_name** – удаление (delete) ветки с именем branch_name
4. **git checkout branch_name** – переход в ветку с названием branch_name
5. **git log** - Журнал изменений (перед переключением версии файла в git используйте команду git log, чтобы увидеть количество сохранений). Эта команда показывает все сохранённые изменения от последнего к первому. _**Если мы находимся в ветке с более старыми изменениями, то не сможем увидеть более новые изменения в других ветках. Чтобы увидеть их – необходимо перейти в ветку с последними изменениями**_
6. **git log --graph** – позволяет визуализировать ветки
7. **git merge branch_name** – позволяет произвести слияние веток, при этом происходит слияние указанной ветки, с той, в которой мы сейчас находимся, т.е. вся информация из указанной ветки (branch_name) добавляется в нашу текущую ветку
8. **.gitignore** – данный файл создаётся в репозитории для возможности игнорирования файла, либо группы файлов, которые вы не только не хотите автоматически добавлять в репозиторий, но и видеть в списках неотслеживаемых (а чем взрослее проект, тем больше таких файлов может быть). К таким файлам обычно относятся автоматически генерируемые файлы (различные логи, результаты сборки программ и т.п.). В файл .gitignore добавляются шаблоны соответствующие таким файлам. _**Хорошая практика заключается в настройке файла .gitignore до того, как начать серьёзно работать, это защитит вас от случайного добавления в репозиторий файлов, которых вы там видеть не хотите**_

### _Комбинации команд_

* **git commit –a**  -  сочетает команды add и commit
* **git branch –m** – переименование ветки
* **git checkout –b**  branch_name  -  сочетает команды branch branch_name и checkout branch_name
* **git merge --abort** - эта команда пытается откатить ваше состояние до того, что было до запуска слияния

## Работа с удаленными репозиториями

1. **git clone <https://........>** – позволяет копировать внешний репозиторий на свой ПК (она не только загружает все изменения, но и пытается слить все ветки на локальном компьютере и в удаленном репозитории)
2. **git push** - позволяет отправить нашу версию репозитория на внешний репозиторий
3. **git pull** - позволяет скачать все из текущего репозитория и автоматически сделать merge с нашей версией _**Требует авторизации**_ на внешнем репозитории
4. **git push -u origin** _Ключ -u (полный вариант --set-upstream) создаёт в удалённом репозитории ветку, соответствующую локальной и связывает их_. (Эта команда используется для отправки закоммиченных файлов в удаленный репозиторий (также известный как GitHub) в указанной ветке)
5. **git remote** позволяет создавать, просматривать и удалять подключения к другим репозиториям
6. **git rm -r — cached** - Эта команда используется для удаления файла из удаленного репозитория (GitHub), не удаляя его в локальном репозитории.
7. **git fetch** Эта команда используется для получения самой последней версии вашего локального репозитория. Загружает коммиты, файлы и ссылки из удаленного репозитория в ваш локальный репозиторий
8. **git reset — hard HEAD** Эта команда удалит все изменения, внесенные вами в ваш локальный репозиторий, и обновит его до последней версии, которая была закоммичена на GitHub
