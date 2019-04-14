﻿## Задание по git 

#### Проверить, что версия git не ниже 2.10.x
```
git --version
```

### 1. Слияние веток без конфликтов (без merge-commit)
```
Создать ветку main1 из ветки main
Сделать merge ветки feature1 в ветку main1
```

### 2. Слияние веток без конфликтов (с merge-commit)
```
Создать ветку main2 из ветки main
Сделать merge ветки feature1 в ветку main2 с флагом no-fast-forward
```

### 3. Наложение изменений поверх ветки без конфликтов
```
Создать ветку main3 из ветки main
Сделать rebase ветки main3 на основании ветки feature1
```

### 4. Слияние избранных коммитов в ветку c конфликтами
```
Создать ветку main4 из ветки main
Сделать cherry-pick последнего коммита из ветки feature2 в ветку main4
```

### 5. Слияние веток с конфликтами
```
Создать ветку feature25 из ветки feature2
Сделать коммит с изменениями данных переменной p1 в Main.java
Сделать merge ветки feature1 в ветку feature25
```

### 6. Наложение изменений поверх ветки с конфликтами
```
Создать ветку feature26 из ветки feature2
Сделать коммит с изменениями данных переменной p1 в Main.java
Сделать rebase ветки feature26 на основании ветки feature1
(после git add * использовать git rebase --continue)
```

### 7. Измение локальной истории коммитов (объединение коммитов)
```Cоздать ветку feature3
Cделать в ветке feature3 два коммита
Вывести инфо о коммитах (git log)
Объединить два последних коммита в один (squash), присвоив новый commit-message 
Снова вывести инфо о коммитах (git log)
```

### 8. Добавление клиентского хука для проверки формата описаний коммитов
```
Разработать хук commit-msg и поместить в директорию .git/hooks
Хук должен возвращать 0, если сообщение соответствует маске "[TICKET-123] my commit message" 
	-может меняться номер тикета и текст сообщения; 
	-номер может быть числом от 1 до 999; 
	-сообщение должно содержать хотя бы один символ; 
	-сообщение и закрывающая скобка разделены пробелом;
	-сообщение должно начинаться с открывающей скобки.
Хук возвращает 1 во всех остальных случаях
Хук нужно написать на bash, используя grep с опциями -iqE
```

## Задание по maven

### 1. Установить maven 
Скачать установщик, установить. 
Прописать переменные среды: 
M2_HOME={путь до папки maven}
Path=%Path%:%M2_HOME%\bin
Проверить правильность установки
´´´ mvn —version ´´´

### 2. Инсталлировать архетипы
Перейти в репозиторий (директорию) SBT-MEPhI (или клонировать его заново)
Скачать изменения из удаленного репозитория
´´´ git fetch ´´´
Перейти в ветку company-archetype. 
Инсталлировать архетип company-archetype в локальный репозиторий
´´´ 
cd company-archetype
mvn clean install 
´´´

### 3. Создать проект из архетипа company-archetype
´´´ mvn archetype:generate -DarchetypeGroupId=ru.sbt.sbt-mephi -DarchetypeArtifactId=company-archetype -DarchetypeVersion=1.0 ´´´

### 4. Скомпилировать проект
Перейти в директорию с созданным проектом (artifactId)
Скомпилировать проект, добавив необходимые зависимости в pom.xml.
GAV (groupId:artifactId:version) зависимостей найти в интернете. 
´´´ mvn clean compile ´´´

### 5. Инсталлировать проект в локальный репозиторий 
´´´ mvn clean install ´´´
Убедиться, что артефакт есть в локальном репозитории. 
Узнать путь до локального репозитория
´´´ mvn help:evaluate -Dexpression=settings.localRepository ´´´

### 6. Разбить проект на три модуля
Создать три папки, в каждую папку добавить pom.xml. 
Перенести каждый класс в отдельный модуль. 
Вынести зависимости из родительского pom.xml в дочерние. 
Версию логгера вынести в property родительского pom.xml. 
Инсталлировать проект в локальный репозиторий. 

### 7. Сконфигурировать сборку 
Добавить в блок build родительского pom.xml конфигурацию для создания sources.jar. 
Добавить профайл, в котором указать mainClass для manifest собираемого jar. 
Собрать проект
´´´ mvn clean package ´´´
Запустить собранный jar
´´´ java -jar ./target/{artifactId}-{version}.jar ´´´

