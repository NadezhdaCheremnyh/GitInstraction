![Git-Logo](Logo_git.jpg)
# Работа с Git
## 1. Проверка наличия установленного Git
В терминале выполнить команду: `git version`
Если Git установлен, появится сообщение с информацией о версии программы. Иначе будет сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию **Git** с сайта https://git-scm.com/downloads
Устанавливаем с настройками по умолчанию

## 3. Настройка Git
При первом использовании **Git** необходимо представиться. Для этого нужно ввести в терминале 2 команды:
```
git config --global user.name «Ваше имя»
git config --global user.email "ваша_почта@example.com"
```
## 4. Инициализация репозитория
В терминале переходим к папке, в которой хотим создать репозиторий. Выполняем команду `git init`
В исходной папке появится скрытая папка *.git*

## 5. Добавление нового файла в репозиторий
В исходной папке создаем новый файл с расширением `.md` <имя файла.md> Созданный файл откроется в рабочей области справа для дальнейшей работы с ним.

## 6. Запись изменений в репозиторий
### 6.1. Получение информации от Git о его текущем состоянии
В терминале выполняем команду `git status` Если созданный файл `.md` не является отслеживаемым (untracked file), то **Git** предложит сделать его отслеживаемым, т.е. включить этот файл к дальнейшей фиксации.
### 6.2. Добавление файла отслеживания
Добавление файла отслеживания или подготовка его к последующей фиксации осуществляется с помощью команды `git add имя_файла.md` Это промежуточное состояние файла `.md`, когда текущему изменению присваивается системный хеш-код (индекс), который в дальнейшем позволит перемещаться между разными фиксациями.
### 6.3. Создание коммита
Создание коммита или фиксация изменения осуществляется с помощью команды `git commit -m "message"`, где параметр `message` содержит текст сообщения о созданном изменении. Команда позволяет зафиксировать изменения и сообщить о появлении новой версии файла отслеживания.
### 6.4. Отображение разницы между текущей и зафиксированной ранее версией файла
В терминале выполним команду `git diff` Если до выполнения этой команды не была выполнена команда `git commit -m "message"`, то текущее изменение файла не зафиксировано, разницу между этой текущей и уже зафиксированной ранее версией файла позволяет увидеть команда `git diff`

## 7. Просмотр истории коммитов
При выполнении в терминале команды `git log` увидим журнал изменений - вывод на экран истории всех коммитов (фиксаций) с их хеш-кодами. Также можно вывести сокращенный журнал изменений с помощью команды `git log --oneline`

## 8. Перемещение между сохранениями
Перемещение между сохранениями или переход от одного коммита к другому осуществляется с помощью команды `git checkout [хеш-код]`, где `[хеш-код]` - системный код, соответствующий каждому коммиту, сформированный командой `git log` Чтобы вернуться и продолжить работу с актуальным состоянием файла, нужно выполнить команду `git checkout master`

## 9. Игнорирование файлов
Для того, чтобы исключить из отслеживания в репозитории определенные файлы или папки, необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны, соответствующие таким файлам или папкам.

## 10. Создание веток в Git
Ветка в Git - это простой перемещаемый указатель на один из коммитов, обычно последний в цепочке коммитов. По умолчанию имя основной ветки в Git - `master`
Создать ветку в Git можно командой:
```
git branch <имя новой ветки>
```
В результате создается новый указатель на текущий коммит. Список веток в репозитории можно посмотреть с помощью команды `git branch` 
Для переключения между ветками используется команда `git checkout <имя ветки>` 
Чтобы при создании ветки сразу на нее переключиться, можно использовать команды:
```
git checkout -b <имя новой ветки>
```
или
```
git switch -c <имя новой ветки>
```

## 11. Слияние веток и разрешение конфликтов
Для слияния выбранной ветки с текущей нужно выполнить команду:
```
git merge <название выбранной ветки>
```

Если была изменена одна и та же часть файла в обеих ветках, то может возникнуть конфликт, который потребует участия пользователя. **Git** предлагает варианты разрешения:
```
Accept Current Change (Применить текущее изменение)

Accept Incomming Change (Применить внешнее изменение)

Accept Both Changes (Применить оба варианта)

Compare Changes (Сравнить изменения)
```
Чтобы разрешить конфликт, нужно выбрать один из вариантов, либо объединить содержимое по-своему.

После разрешения конфликта нужно выполнить коммит слияния, например:
```
git commit -a -m "Merge branch <выбранная ветка>"
```

## 12. Удаление веток
После выполнения слияния веток, ненужную ветку можно удалить командой:
```
git branch -d <название ветки>
```
Если мы удаляем ветку, не сделав слияния, **Git** выдает сообщение об ошибке и предлагает выполнить следующую команду, если все равно хотим удалить:
```
git branch -D <название ветки>
```

## 13. Работа с удаленными репозиториями


![Git-img](img_github.jpg)

**1.** Создаем аккаунт на https://github.com

**2.** Создаем локальный репозиторий

**3.** Создаем новый репозиторий на **GitHub** в своем аккаунте. При создании нового репозитория, **GitHub** предлагает несколько вариантов. 
Чтобы "подружить" наш локальный и удаленный репозитории, нужно выбрать вариант:
```
...or push an existing repository from the command line
```
и поочередно выполнить в **Git** следующие команды:
1. Привязать локальный репозиторий с удаленным:
```
git remote add origin <url-адрес>

где <url-адрес> -адрес внешнего репозитория на Github
```
2. Переименовать текущую ветку `master` в ветку `main`
```
git branch -M main
```
3. Отправить изменения, сделанные в локальном репозитории на удаленный
```
git push -u origin main
```
**4.** Отправить нашу локальную версию репозитория на удаленный репозиторий (на **Github**) можно с помощью команды
```
git push
```
(возможно, потребуется авторизация на внешнем репозитории)

**5.** Получить изменения с удаленного репозитория (на **Github**) и слить их с локальной версией можно с помощью команды
```
git pull
```
**6.** Клонирование любого внешнего репозитория на наш ПК осуществляется командой 
```
git clone <url-адрес>

где <url-адрес> -адрес внешнего репозитория на Github
```
## 14. Pull request

Для перехода в клонированный (командой `clone`) репозиторий необходимо выполнить команду:
```
cd <имя_файла.git>

где <имя_файла.git> -имя внешнего репозитория
```
Для внесения изменений в клонированный файл  создаем новую ветку и переходим на нее. Создаем новый отслеживаемый файл `имя_файла.md` и заполняем его информацией и фиксируем изменения командами:
```
git add имя_файла.md
git commit -m "message"
```
Отправляем измененный файл на **Github** командой 
```
git push
```
На сайте **GitHub** выполнить [Pull request] 
