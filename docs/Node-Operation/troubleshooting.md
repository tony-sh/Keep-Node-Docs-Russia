# Исправление проблем

В этом разделе показано, как бороться с некоторыми распространенными ошибками и предупреждениями, а также как их устранять.

**Содержание раздела**
- [Introduction and Log Access (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Troubleshooting#introduction-and-log-access)
- [Common Errors and Warnings (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Troubleshooting#common-errors-and-warnings) 
    - [Just ignore these WARNINGS (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Troubleshooting#just-ignore-these-warnings)
    - [Config.toml File errors (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Troubleshooting#configtoml-file-errors)
    - [Errors after updating addresses inside Config.toml (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Troubleshooting#errors-after-updating-addresses-inside-configtoml)
    - [Errors from Token Delegation / Contracts authorization (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Troubleshooting#errors-from-token-delegation--contracts-authorization)
- [Other Warnings (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Troubleshooting#other-warnings)

## Введение и доступ к логам
**Прежде всего: убедитесь, что вы используете последние версии клиентов с последними контрактами. Подключив одноранговые ноды + запросы infura.**

Вы можете проверить логи для каждой ноды с помощью этой команды: `docker logs *node-name*`
Вы можете определить имя ноды командой `docker ps` (last column -> names)
Вы также можете увидеть некоторые другие распространенные способы получения конкретной информации из логов с помощью [этих команд](https://github.com/Estebank97/Keep-Node-Operation/wiki/Manage-your-Nodes#ecdsa-node-maintenance)

Если вы видите подключенные пиры - всё ок:

<p align="center">
  <img width="719" alt="Intro" src="https://user-images.githubusercontent.com/68087535/89208516-e7419d80-d592-11ea-9822-13be0ae02cb1.png">
</p>

В этом примере [27] подключенных пиров.


## Общие ошибки и предупреждения
Если вы видите подключенные пиры - ваша нода работает.

С другой стороны, если вы видите CRITICAL или WARNING , возможно, ваша нода не работает должным образом.
Давайте посмотрим на несколько распространенных примеров и укажем способ их решения :

### Просто игнорируйте эти WARNINGS

<p align="center">
  <img width="719" alt="Ignore" src="https://user-images.githubusercontent.com/68087535/89208525-ec9ee800-d592-11ea-8836-ac5276be14b9.png">
</p>
Невозможно установить соединение с каким-то конкретным пиром, это не должно быть проблемой… Как видите, вы подключили 71 пир, так что все в порядке!

### Config.toml ошибка файла
Проверьте ваш config.toml возможно там есть грамматические ошибки:
<p align="center">
  <img width="719" alt="config" src="https://user-images.githubusercontent.com/68087535/89208529-ee68ab80-d592-11ea-944e-c6538db35110.png">
</p>


Убедитесь, что вы правильно установили пароль, в `export KEEP_CLIENT_ETHEREUM_PASSWORD="your_eth_wallet_password"` :
<p align="center">
  <img width="719" alt="pass1" src="https://user-images.githubusercontent.com/68087535/89208536-f1fc3280-d592-11ea-9977-0d9bb22dfc9a.png">
</p>



Здесь показаны контракты, которые определены в файле Config.toml. Убедитесь, что у вас есть последние обновления. (Вы можете дважды проверить закрепленные сообщения в канале Discord или в Github (https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc) :

<p align="center">
  <img width="719" alt="contract1" src="https://user-images.githubusercontent.com/68087535/89208553-f4f72300-d592-11ea-8784-0e055f75ed6b.png">
</p>

### Ошибки после обновления адресов внутри Config.toml 
Время от времени необходимо выполнять некоторые обновления ноды, например когда Keep Team обновляет адреса контрактов :
<p align="center">
  <img width="750" alt="contract2" src="https://user-images.githubusercontent.com/68087535/89208558-f6285000-d592-11ea-942b-a22477b3b5f1.png">
</p>
In this example the addresses where changed at the wrong spot inside Config.toml.


### Ошибки с Token Delegation / Contracts authorization
<p align="center">
  <img width="719" alt="Autho" src="https://user-images.githubusercontent.com/68087535/89208564-f7597d00-d592-11ea-8c88-ec94438bb1d5.png">
</p>
Вам нужно перейти в Keep Token app и проверить, отсутствует ли делегирование токена или авторизация контрактов.


## Другие предупреждения
<p align="center">
  <img width="719" alt="Other 1" src="https://user-images.githubusercontent.com/68087535/89208567-f7f21380-d592-11ea-9c87-71cd7227bf5f.png">
</p>
Какая-то проблема с хранением контрактов в сети Keep, с этим ничего не поделать.

<p align="center">
  <img width="719" alt="Other 2" src="https://user-images.githubusercontent.com/68087535/89208572-f9bbd700-d592-11ea-86ed-409db54acde8.png">
</p>
Проблема в цепочке, как-то связана с попыткой присоединиться к объединенному пулу жеребьевки.



!> @Nico186 сделал отличный [документ](https://docs.google.com/document/u/2/d/e/2PACX-1vRYtVyLSwuNBL9Xk-M1HeHloJ7MIGqwiEzsuXYnKHQqnSz2gfd2Q3czJeOzEferPKIr7GvIznQxsckb/pub) с интерпретацией логов ошибок и предупреждений KEEP.

---
`Источник из официальной документации Keep Team, отредактированный и дополненный сообществом. '[Источник] (https://keep-network.gitbook.io/staking-documentation/)`

`Авторы: Ramaruro, EstebanK`
`Перевод: tony__s_h`
