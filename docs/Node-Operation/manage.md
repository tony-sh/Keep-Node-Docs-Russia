# Управление нодами
В этом разделе рассматриваются вопросы управления нодами: после настройки и запуска, вы должны контролировать их работу и обновлять их всякий раз, когда команда Keep запускает новые контракты или новые версии клиентов.

## Лучшие рекомендации


### Отдельные INFURA аккаунты

Создайте один проект INFURA для каждой еоды, чтобы видеть отдельные действия для каждого проекта.
Это быстрый и простой способ проверить активность нод, но это не должно быть основным способом проверки.
<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88484551-07d77b00-cf35-11ea-974e-5dddd0162bab.png">
</p>


### Используйте разные Virtual Private Server (VPS) для нод

Хотя это увеличивает стоимость эксплуатации, если возникают проблемы с операциями или обновлениями, вы можете грамотней распределить риски.

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88492899-be5a5080-cf73-11ea-972d-715dca658e0c.png">
</p>

## Проверка работоспособности ноды

!>**@Herobrine** сделал потрясающее приложение, которое вы можете запустить, чтобы проверить работоспособность ноды: [KeepNode.app](https://keepnode.app/)

### Обслуживание ECDSA ноды

Основная проверка, которую вы должны сделать, это убедиться, что нода ECDSA подключена к пирам:

Используйте терминал: `sudo docker logs ecdsa --since 5m | grep "connected"`

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88097681-2668fb00-cb5e-11ea-94d4-c080e20d5a15.png">
</p>

Вы также можете проверить Keep Creation.

Используйте терминал: `sudo docker logs ecdsa 2>&1 | grep "new keep"`

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88484709-30ac4000-cf36-11ea-8baf-3a54b48523b2.png">
</p>

Посмотреть лог "подключенных" пиров

Используйте терминал: `sudo docker logs ecdsa --since 5m | grep "connected"`

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88487822-226a1e00-cf4e-11ea-8351-60cf0a68d968.png">
</p>


!> Если запущены ноды в основной сети, обязательно выполните шаги - [Mainnet Node Operation Section](https://estebank97.github.io/Keep-Node-Docs/#/Node-Operation/mainnet) и используйте [Community Tools](https://estebank97.github.io/Keep-Node-Docs/#/basics/tools). 


## Недостаточное обеспечение и ликвидация

Существует серьезный риск того, что из-за относительных колебаний цен пары ETH / BTC ваше обеспечение (фактически, залог для Keep (ов), который вы подписали) окажется недостаточным, и вы подвергнетесь риску ликвидации.
Процесс подробно описан в [tBTC System Design Document](https://docs.keep.network/tbtc/index.pdf), страницы 19-20

Статья от Bison Trail, [Keep Active Management](https://bisontrails.co/keep-active-participation/), объясняет этот процесс ликвидации и перечисляет несколько мер, которые можно предпринять, чтобы избежать этой проблемы.

В настоящее время мониторинг должен быть ручным, то есть проверка относительных колебаний цен ETH / BTC и добавления залога ETH.

[Latenthero](https://discord.com/channels/590951101600235531/590951101600235533/737707953221664779) создал [Telegram Bot](https://t.me/keep_alert_bot) для предупреждения, когда доступный ETH ниже установленного пользователем порога. Код для бота можно увидеть и в конечном итоге перепрофилировать [тут](https://github.com/latenthero/keep-alert-bot). Он доступен для Testnet с августа 2020 года.

Этот документ от Experience#2376 предоставляет более подробную информацию со ссылками на задействованный программный код: [tBTC risk - liquidation and slashing details](https://hackmd.io/OzIeyWcfTVO69zIF67XCkg). Этот график из документа хорошо объясняет риски.
<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88967178-0975ab80-d273-11ea-9696-15f2ce8995c5.png">
</p>

h/t ssh


## Обновление нод
Время от времени команда разработчиков Keep будет выпускать новые образы Docker для обоих нод и обновлять соответствующие контракты Ethereum.

### Основные выдержки из гайда по обновлениям

Время от времени команда разработчиков Keep будет выпускать новые образы Docker для обоих нод и обновлять соответствующие контракты Ethereum. Смотрите этот [Run ECDSA Keep](https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc#83-authorizations) документ.
Вам необходимо сделать следующее:
* Остановите ноду --> `sudo docker stop ecdsa`
* Отредактируйте файл "config.toml" --> `nano $HOME/keep-ecdsa/config/config.toml`
* Обновите контракты и списки партнеров, как указано командой Keep
  - Например, это обновление контрактов и списка пиров было сделано в июне 2020 года (выделено зеленым цветом).

<p align="center">
  <img width="900" src="https://user-images.githubusercontent.com/68167410/88488480-0026cf00-cf53-11ea-9ef6-cf65551f5cb1.png">
</p>

Как альернативу можно использовать гайд - **Papyasha** [Update Nodes](https://gist.github.com/papyasha/7d97cb53aa1153cc65b0535c2b9f23e3) показывает чистый способ обновления файлов конфигурации путем их удаления и повторного запуска. Он также включает ссылку на исходный запуск нод со всеми необходимыми деталями.

---
### Обновление 2 сентября 2020 г. (+ 8 сентября)
Ключевые действия по обновлению обоих нод следующие:
* Получите новый грант KEEP Tokens для Testnet Faucet:
  - https://us-central1-keep-test-f3e0.cloudfunctions.net/keep-faucet-ropsten?account= **`"Your Operator Ethereum Address"`**
* Стейкните грант в [KEEP Dapp](https://dashboard.test.keep.network/tokens/overview) (this address for Testnet)
* Авторизуйте контракты KEEP Dapp
  - Авторизуйте [Random Beacon](https://dashboard.test.keep.network/applications/random-beacon)
  - Авторизуйте [ECDSA](https://dashboard.test.keep.network/applications/tbtc) and add ETH for Bonding
* Остановка Docker Containers :
  - Убедитесь что указали корректные имена -  `sudo docker ps`.
  - для Random Beacon: `sudo docker stop keep-client`
  - для ECDSA: `sudo docker stop ecdsa` 
* Удалите Current Containers :
  - для Random Beacon: `sudo docker rm keep-client`
  - для ECDSA: `sudo docker rm ecdsa`
* Загрузите New Docker Images :
  - для Random Beacon: `sudo docker pull keepnetwork/keep-client:v1.3.0-rc.4`
  - для ECDSA: `sudo docker pull keepnetwork/keep-ecdsa-client:v1.2.0-rc.5`
* Обновите Config.toml :
  - Если обе  ноды работают на одном VPS, помните, что каждый файл конфигурации находится в отдельной папке. В этом примере названы keep-client и keep-ecdsa.
  - Убедитесь что указали корректные имена папок `ls`.
  - для Random Beacon:`nano $HOME/keep-client/config/config.toml`
     - KeepRandomBeaconOperator = `"0xC8337a94a50d16191513dEF4D1e61A6886BF410f"`
     - TokenStaking = `"0x234d2182B29c6a64ce3ab6940037b5C8FdAB608e"`
     - KeepRandomBeaconService = `"0x6c04499B595efdc28CdbEd3f9ed2E83d7dCCC717"`
  - для ECDSA:`nano $HOME/keep-ecdsa/config/config.toml`
     - BondedECDSAKeepFactory = `“0x9EcCf03dFBDa6A5E50d7aBA14e0c60c2F6c575E6”`
     - Sanctioned Applications = `“0xc3f96306eDabACEa249D2D22Ec65697f38c6Da69”`
* Запустите Docker Containers :
- Запишите это как одну команду и помните, что она может измениться в соответствии с руководством, которое вы использовали изначально (например, порты могут отличаться от 3919: 3919).
  - Убедитесь, что вы ссылаетесь на новые образы Docker и запускаете каждый в своей папке (если на том же VPS)!
  
  
  - для Random Beacon:
  
  
        sudo docker run -dit
        --restart always
        --volume $HOME/keep-client:/mnt      
        --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD     
        --env LOG_LEVEL=debug     
        --log-opt max-size=100m     
        --log-opt max-file=3     
        --name keep-client     
        -p 3919:3919 
        keepnetwork/keep-client:v1.3.0-rc.4 --config /mnt/config/config.toml start
      
      
  - для ECDSA: 
  
  
        sudo docker run -d     
        --restart always     
        --entrypoint /usr/local/bin/keep-ecdsa     
        --volume $HOME/keep-ecdsa:/mnt/keep-ecdsa     
        --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD     
        --env LOG_LEVEL=debug     
        --log-opt max-size=100m     
        --log-opt max-file=3     
        --name ecdsa 
        -p 3919:3919 
        keepnetwork/keep-ecdsa-client:v1.2.0-rc.5 --config /mnt/keep-ecdsa/config/config.toml start

* Проверьте логи на подключения пиров :
  - для Random Beacon: `sudo docker logs keep-client 2>&1 --since 5m | grep "number of connected peers"`
  - для ECDSA: `sudo docker logs ecdsa 2>&1 --since 5m | grep "number of connected peers"`
  - Если он показывает какие-то ошибки, сначала убедитесь, что контракты авторизованы в дашборде. Иногда нужно повторить всё снова.

* Наконец, не забудьте добавить тестовый ETH к привязке tBTC в дашборде!


---
### Август 7, 2020 Обновление
Ключевые действия по обновлению обоих нод следующие:
* Получите новый грат KEEP Tokens для Testnet Faucet:
  - https://us-central1-keep-test-f3e0.cloudfunctions.net/keep-faucet-ropsten?account= **`"Your Operator Ethereum Address"`**
* Застейкайте его в [KEEP Dapp](https://dashboard.test.keep.network/tokens/overview) (this address for Testnet)
* Авторизуйте контракты в KEEP Dapp
  - Авторизуйте [Random Beacon](https://dashboard.test.keep.network/applications/random-beacon)
  - Авторизуйте [ECDSA](https://dashboard.test.keep.network/applications/tbtc) and add ETH for Bonding
* Остановите Docker Containers :
  - Убедитесь что указали корректные имена -  `sudo docker ps`.
  - для Random Beacon: `sudo docker stop keep-client`
  - для ECDSA: `sudo docker stop ecdsa` 
* Удалите Current Containers :
  - для Random Beacon: `sudo docker rm keep-client`
  - для ECDSA: `sudo docker rm ecdsa`
* Загрузите New Docker Images :
  - для Random Beacon: `sudo docker pull keepnetwork/keep-client:v1.3.0-rc`
  - для ECDSA: `sudo docker pull keepnetwork/keep-ecdsa-client:v1.2.0-rc`
* Обновите Config.toml :
  - Если обе  ноды работают на одном VPS, помните, что каждый файл конфигурации находится в отдельной папке. В этом примере названы keep-client и keep-ecdsa.
  - Убедитесь что указали корректные имена папок `ls`.
  - для Random Beacon:`nano $HOME/keep-client/config/config.toml`
     - KeepRandomBeaconOperator = `"0xf417b31104631280adF9F6828ee19985BC299fdC"`
     - TokenStaking = `"0x8117632eC1D514550b3880Bc68F9AC1A76c9C67B"`
     - KeepRandomBeaconService = `"0xd83248e311DC2Ba0d2A051e86f0678d8857f6ADD`"
  - для ECDSA:`nano $HOME/keep-ecdsa/config/config.toml`
     - BondedECDSAKeepFactory = `“0xb37c8696cD023c11357B37b5b12A9884c9C83784”`
     - Sanctioned Applications = `“0x9F3B3bCED0AFfe862D436CB8FF462a454040Af80”`
* Запустите Docker Containers :
  -  Запишите это как одну команду и помните, что она может измениться в соответствии с руководством, которое вы использовали изначально (например, порты могут отличаться от 3919: 3919).
  
  - для Random Beacon: `sudo docker run -dit --restart always --volume $HOME/keep-client:/mnt --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD --env LOG_LEVEL=debug --log-opt max-size=100m --log-opt max-file=3 --name keep-client -p 3919:3919 keepnetwork/keep-client:v1.3.0-rc --config  /mnt/config/config.toml start`
  - для ECDSA: `sudo docker run -d    --restart always    --entrypoint /usr/local/bin/keep-ecdsa    --volume $HOME/keep-ecdsa:/mnt/keep-ecdsa    --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD    --env LOG_LEVEL=debug    --log-opt max-size=100m    --log-opt max-file=3     --name ecdsa -p 3919:3919 keepnetwork/keep-ecdsa-client:v1.2.0-rc    --config /mnt/keep-ecdsa/config/config.toml start`

* Проверьте логи на подключения пиров :
  - для Random Beacon: `sudo docker logs keep-client 2>&1 --since 5m | grep "number of connected peers"`
  - для ECDSA: `sudo docker logs ecdsa 2>&1 --since 5m | grep "number of connected peers"`
  - Если он показывает какие-то ошибки, сначала убедитесь, что контракты авторизованы в дашборде. Иногда нужно повторить всё снова.

* Наконец, не забудьте добавить тестовый ETH к привязке tBTC в дашборде!

---
`Источник из официальной документации Keep Team, отредактированный и дополненный сообществом. '[Источник] (https://keep-network.gitbook.io/staking-documentation/)`

`Авторы: Ramaruro, EstebanK`
`Перевод: tony__s_h`

