#### Описание
Shell скрипты, которые собирают билд, для Android приложений `ramc-cli`, `ramc-par`.

#### Генерирование приложения для клиентов
Запустить скрипт из командной строки, указав в параметрах требуемые значения,
для генерирования кастомного билда:
`$ ./generate-ramc-cli.sh -n <NAME> -l <PATH_TO_LOGO_IMAGE> -f <FAIL_MESSAGE> -i <INFO_MESSAGE> -p <SUPPORT_PHONE>`

где:

- `<NAME>` имя билда
- `<PATH_TO_LOGO_IMAGE>` путь к картинке с логотипом
- `<FAIL_MESSAGE>` сообщение показывающееся пользователю при невозможности
  отправки заявки на сервер
- `<INFO_MESSAGE>` информационное сообщение отображаемое на экране "Информация"
- `<SUPPORT_PHONE>` телефон службы поддержки клиентов

порядок следования параметров не важен,
важно их общее присутствие.

Сгенерированые билды будут находиться в папке `gen-cli/<NAME>`.

Исходный код Android приложения для клиентов должен находиться в папке `ramc-cli`.

#### Генерирование приложения для партнеров
Запустить скрипт из командной строки, указав в параметрах требуемые значения,
для генерирования кастомного билда:
`$ ./generate-ramc-par.sh -n <NAME> -p <PARTNER_ID>`

где:

- `<NAME>` имя билда
- `<PARTNER_ID>` идентификационный номер партнера

порядок следования параметров не важен,
важно их общее присутствие.

Сгенерированые билды будут находиться в папке `gen-par/<NAME>`.

Исходный код Android приложения для партнеров должен находиться в папке `ramc-par`.

#### Запуск сервера
Изменить настройки для подключения к БД в `server/pg_conf.js`.

В директории `server` выполнить команду `NODE_ENV=production node app.js`
или например `NODE_ENV=production forever start -m 5 app.js`.

Сгенерированные, пользователями веб-интерфейса, билды будут храниться в
директориях `server/public/build/gen-cli/` и `server/public/build/gen-par/` для
клиентских и партнёрских приложений соответствено.

#### Установка зависимостей

- Установить Java SE Development Kit (от Oracle)
  
  после установки выполнить `sudo update-alternatives --config java`
  если в системе установленно несколько вариантов для `java`

- Установить Android SDK Tools
  
  скачать `android-sdk_r22.0.1-linux.tgz` и распаковать архив в `android-sdk`
  
  прописать переменные среды:
    `export ANDROID_SDK=~/android-sdk`
    `PATH=$PATH:$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools`
  
  установить `SDK Platform Android 4.2.2, API 17`, `Android SDK Platform-tools`, `Android SDK Build-tools`, `Android Support Library` командой
  `android update sdk -u --filter <номера>`,
  где `<номера>` номера перечисленных выше компонентов из команды `android list sdk`
  
- Установить `ant`

- Установить `Node.js`
