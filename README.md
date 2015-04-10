Скрипт для загрузки внешних .rb файлов для Rpg Maker VX ACE
Позволяет подключать внешние скрипты, загружать папки со скриптами целиком, подключать простые гемы (без extension)
Так же по умолчанию сливает все подключенные скрипты в один файл batch.rb, который находится в корне проекта.

###Как использовать:
* Добавте скрипт в мейкер
* Для подключения гемов:
  - Создайте папку gems в корне проекта
  - Скачайте гем и поместите в папку gems (обычно к названию папки гема добавляют версию, лучше ее убрать)
  - После скрипта
  ```
  SideScriptsLoader.add_gems_to_path
  require 'gem_name' #имя папки гема в дирректории gems
  ```
  - Обратите внимание, что многие стандартные модули и классы вырезаны в мейкере. Многие гемы делают require таких модулей, и это вызовет эксепшн в вашей игре. Каждый такой случай необходимо разбирать и фиксить отдельно. Так же в папку gems нужно поместить все зависимости гема, если такие есть.
* Для добавление папки в $LOAD_PATH (дирректория должна лежать в корне проекта)
  ```
  SideScriptsLoader.add_to_path 'dir_name'
  ```
* Для загрузки файлов целой папки (дирректория должна лежать в корне проекта):
  ```
  SideScriptsLoader.load 'dir_name'
  ```
* Комбинируя `add_to_path` и `load` можно добиться загрузки всех файлов из папки, при этом все вызовы require в этих файлах так же будут работать:
  ```
  SideScriptsLoader.add_to_path 'dir_name'
  SideScriptsLoader.load 'lib'
  ```
* Для отключения функции слияние всех скриптов в файл batch.rb
```
class RequireLoader
  #set to false if you do not want to compress 
  #all the scripts to batch.rb file 
  BATCH =  false
  ...
end
```
