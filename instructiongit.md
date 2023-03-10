# **Интсрукция работы с Git**
## Создание репозитория
Для создания(инициализации) нового репозитория нужно находясь в соответсвующей папке через термина ввести команду:

    git init

## Добавление файлов к отслеживанию:
Для добавления файлов к отслеживанию необходимо использовать комнаду:

    git add filename

Где *filename* - имя добавляемого файла.

Премичание: данную команду необходимо выполнить перед командой *git commit* (в случае если комманда git commit вызывается без флага a)
## Создание коммита
Для создания коммита необходимо выполнить следующую команду:

    git commit
Если ввести её в таком виде, то появится текстовый редактор для ввода комментария(сообщения) к коммиту. **ОНО ОБЯЗАТЕЛЬНО**, без него коммит **не будет** создан.
Для того чтобы текстовый редактор не открывался, можно записать эту команду с флагом -m:

    git commit -m "ваше сообщение"
Флаг -a для комманды *git commit* используется, чтобы автоматически выполнить комманду *git add .* перед командой *git commit*
    
    git commit -a 

В данном случае результат будет аналогичен команде git commit(с автоматическим добавлением файлов к отслеживанию)

Так существует комбинация флагов -a и -m, записывается так:
    
    git commit -am "Ваше сообщение"
**ВАЖНО**: НЕ ЗАБЫВАТЬ СОХРАНЯТЬ ФАЙЛ ПЕРЕД СОЗДАНИЕМ КОММИТА
## История коммитов:
Для получения истории коммитов, нужно выполнить комнаду:
    
     git log

Данная команда выдаст результат, следующего вида(для каждого коммита):

    commit %hash%
    Author: %your_name% <%your_email%>
    Date:   дата и время коммита

        Ваше Сообщение коммиту

Где, %hash% - хеш коммита, он нужен для команды *git checkout*

%your_name% - ваше имя, указанное при настройке

%your_email% - ваша почта указанная при настройке

Опции:
* опция --all, нужна для отображения всех коммитов на всех ветках, пример:
    git log --all
* опция --oneline нужна для более краткого отображения
* опция --graph - нужна для наглядного отображения коммитов (в виде графа)
* опции --graph и --all можно комбинировать
* эти две опции можно комбинировать пример: *git log --all --oneline* или *git log --oneline --all*

В случае использования опции --oneline, вывод преобретает следующий вид:

    8b1be8a (HEAD -> master) Info about command git diff added
    9c392ae info about command git checkout added
    496549c info about command git status added
    957df9a Info about command git log added
    4a249e5 Info about command git commit added
    a6b67ea Info about command git add added
    bc355f5 Info about command git init added
    b3e20fe main header added
    11eb173 Init commit
Где, первые цифры буквы - первая часть хэша(так же может использоваться в качестве аргумента для команды *git checkout*), а текст - то самое сообщение, при создания коммита
## Получения статуса репозитория:
Для получения статуса репозитория нужно выполнить команду:

    git status
Она выдаст следующую информацию:
* на какой ветке вы находитесь
* Какие файлы изменены
* Какие файлы удалены
* Какие файлы созданы(они будут неотслеживаемыми)
Если никаких изменний репозитория нет, то она выдаст что нечего коммитить.
## Переключение на ранний коммит:
Для переключения на ранний коммит вам потребуется команда:
  
    git checkout %hash%
  
  Где, %hash% - хэш интересующего вас коммита, полученный через команду *git log*

Для того чтобы вернутся к последней версии, требуется написать:

    git checkout branch_name

Где, branch_name - имя ветки, на которой вы работали.
Так же, команда:

    git checkout branch_name
  Позволяет вам переключится на любую ветку, для этого вместо branch_name нужно просто написать имя ветки, на которую вы хотите переключится.

  **ВАЖНО**: нужно чтобы перед переключением на другую ветку в этой ветке было нечего коммитить.
**Премичание**, перед переключением на ранний коммит нужно закоммитить текущие изменения, если они есть.
## Просмотр разницы между текущим коммитом и внесёнными изменниями
Для просмотра разницы между текущим коммитом и не зафиксированными изменениями существует команда:

    git diff

Она отобразит что было добавлено в файлы, а что было удалено.

**ВАЖНО**: чтобы команда git diff показала разницу нужно **сохранить** файл
## Ветвленщие в git
Ветвления нужны для того, чтобы иметь возможность:
* работать с несколькими вариантами решения одной задаычи, а потом выбрать из них лучшее
* сохранения рабочей версии проекта и внесения основных изменений в отдельную ветку, чтобы не портить рабочую версию
* организации командной работы над проектом(когда работа над разными частями проекта происходит в разных ветках)
### Просмотр всех веток

Для просмотра списка всех имеющихся веток нужно ввести команду:

    git branch
  Она выдаст список всех веток и рядом с текущей веткой будет стоять звёздочка
  Результат будет примерно таким:
    
    * master
    branching
  В данном случае у нас есть две ветки, branching и master, master - активная ветка.
### Создание новой ветки
Для создания новой ветки нужно выполнить следующую команду:
    
    git branch newbranchname
  Где, newbranchname - имя новой ветки

### Удаление ветки
Для удаления ветки нужно выполнить команду:

    git branch -d branch_for_deleting

Где branch_for_deleting - имя ветки для удаления
Так же, если нужно удалить несколько веток, то можно просто перечислить их через пробел:

    git branch -d first_branch_for_deleting second_branch_for_deleting
**ВАЖНО**: перед удалением необходимо убедится что все изменения слиты в какую-нибудь другую ветку, иначе удаления не пройдёт.
## Информация про файл .gitignore
В данный файл вносятся имена файлов или имена папок которые git не должен отслеживать.
Пример содержимого:

    *.jpg
    target/
В данном случае, git будет игнорировать все файлы с расширением .jpg и всё что находится в папке target
## Дополнительная важная информация
git не умеет нормально работать с бинарными файлами(всё кроме текстовых файлов)

 Вот небольшой список таких файлов:

  * картинки
  * вордовские документы в вордовском формате
  * файлы программ (те, которые получаются  на выходе с компилятора)
  
  Как минимум потому, что команда git diff с такими файлами работать нормально не сможет.

  Технически конечно их можно добавить к коммиту, но пользы от этого будет мало
  ## Удалённые репозитории
Это репозитории которые находятся на другом компьютере и к которым есть возможность подключится.
