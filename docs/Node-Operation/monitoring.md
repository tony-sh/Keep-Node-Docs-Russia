# Мониторинг и оповещения

В этом разделе рассматриваются следующие темы, связанные с методами автоматического мониторинга нод и удаленного оповещения.

**Содержание этого раздела**
- [Гайд по настройке мониторинга Keep нод (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Monitoring-and-Remote-Alerting#guides-for-setting-up-node-monitoring-of-keep-nodes)
- [Discord и Telegram боты (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Monitoring-and-Remote-Alerting#discord-and-telegram-bots-to-get-keep-network-stats)

## Гайд по настройке мониторинга Keep нод
### Random Beacon мониторинг, используя Grafana, Prometheus, Prometheus Node Exporter, Google cAdvisor и Loki
- MutedTommy's [Keep Random Beacon | Node Monitoring | Part 1](https://medium.com/@hr12rtk/keep-random-beacon-node-monitoring-grafana-prometheus-and-loki-4a4b669b31ea) and [Part 2](https://medium.com/@hr12rtk/keep-random-beacon-node-monitoring-part-2-5cd037464a6e).
В этой статье кратко описаны шаги для настройки мониторинга на Keep Random Beacon ноде, используя Grafana, Prometheus, Prometheus Node Exporter, Google cAdvisor и Loki.

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/89043879-c537e900-d30e-11ea-84ad-dfbd47592d2f.png">
</p>


### Random Beacon и ECDSA мониторинг нод, используя Elasticsearch, Logstash, и Kibana
- Гайд по [Настройке Elastic Stack Dashboard (англ.)](https://www.notion.so/Setting-up-Elastic-Stack-Dashboard-14f9edc94418468bb95af40417a0332a) для Keep Random Beacon и ECDSA нод, используя Elasticsearch, Logstash, и Kibana

>Elastic Stack — также называемый ELK Stack — это подборка програмного обеспечения с открытым исходным кодом, разработанного Elastic, который позволяет вам искать, анализировать и визуализировать логи, созданные из любого источника в любом формате. Централизованное ведение логов может быть очень полезно при попытке определить проблемы с вашими серверами или приложениями, поскольку оно позволяет вам искать по всем вашим логам в одном месте. Это также полезно, поскольку позволяет выявлять проблемы, охватывающие несколько серверов, путем сопоставления их логов по определенному периоду времени.
>
>[Elastic Stack](https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elastic-stack-on-ubuntu-18-04#step-4-%E2%80%94-installing-and-configuring-filebeat) имеет четыре основных компонента:
>
> Elasticsearch: поисковая система RESTful, в которой хранятся все собранные данные.
>
> Logstash: компонент обработки данных Elastic Stack, который отправляет входящие данные в Elasticsearch.
>
> Kibana: веб-интерфейс для поиска и визуализации логов.
>
> Beats: одноцелевые поставщики данных, которые могут отправлять данные с сотен или тысяч машин в Logstash или Elasticsearch.
>
<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/89001980-816ac280-d2c1-11ea-98f2-94e0481188fc.png">
</p>


## Discord и Telegram для получения статистики от Keep Network
Некоторые боты разработаны для использования в [Keep Discord Channel](https://discord.com/channels/590951101600235531/709789601459339326). В ближайшие месяцы должны появиться обновления.

[KEEP BOT](https://discord.com/channels/590951101600235531/709789601459339326/735597811613302855) by StateLayer 

Список команд для бота
Keep Network Bot (StateLayer)
- !keep all : Show all network stats
- !keep price: $KEEP price
- !keep volume: KEEP 24h volume 
- !keep stakers : number of stakers on the network 
- !keep holders: Amount of holders of KEEP 
- !keep staked: Amount of KEEP staked in the random beacon contract 
- !keep stakedropreserve: Amount of KEEP in the stakedrop reserve 
- !keep liquidityreserve: Amount of KEEP in the liquidity reserve 
- !keep beacontransactions: Total number of random beacon transactions
- !keep exchanges : show keep balances in exchanges
- !keep wen ICO? : (Hint, never)

Мониторинг нод (StateLayer)
 (ЛС боту)
- !watcher summary youraddress : различная статистика о вашей подписывающей группе
- !watcher ethbonded youraddress : получить баланс, связанный с вашей группой
- !watcher collateralratio youraddress : коэффициент залога вашей группы
- !watcher help : показать доступные команды
Вместо "youraddress", вставьте эфириум адресс вашей подписывающей группы.

tBTC статистика (pantsme)
Доступные команды: !supply, !txs, !holders, !tdt, !volume, !help

---
`Источник из официальной документации Keep Team, отредактированный и дополненный сообществом. '[Источник] (https://keep-network.gitbook.io/staking-documentation/)`

`Авторы: Ramaruro, EstebanK`
`Перевод: ingag`

