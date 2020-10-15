# Снижение рисков для операторов нод

Эксплуатация Keep нод сопряжена с рисками, поскольку существуют требования к обеспечению и доступности, которые должны быть выполнены.
В этом разделе рассматриваются темы, связанные с пониманием и снижением рисков, связанных с эксплуатацией Keep Poduction System.

**Содержание этого раздела**
- [Основные риски при эксплуатации Keep нод (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#main-risks-for-operating-keep-nodes)
- [Предотвращение недостаточного обеспечния (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#undercollateralization-prevention) 
- [Высокая доступность (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#main-risks-for-operating-keep-nodes)
    - [Общие соображения о Keep Team (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#general-considerations-from-the-keep-team)
    - [Размещение на базе Kubernetes (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#kubernetes-based-deployment)

## Основные риски при эксплуатации Keep нод
Исходя из текущего понимания и функционирования системы Keep в Testnet, мы видим два основных риска для оператора потерять часть или все средства, вложенные в поддержку моста tBTC:
* Недостаточное обеспечение и ликвидация
* Простой ноды

Текущее понимание указывает на то, что недостаточная обеспеченность является более острой проблемой, чем простои ноды. Время безотказной работы ноды в тестовой сети велико, и, кроме обновлений программного обеспечения или проблем с поставщиком VPS, это не является высоким риском для работы. Риск также может быть смягчен с помощью установки дополнительной ноды, управляемой с помощью Kubernetes (см. ниже).
Однако недостаточное обеспечение кажется более серьезной проблемой, поскольку она менее контролируема, и нет никакого автоматизированного способа исправить ситуацию, кроме ручного вмешательства.


## Предотвращение недостаточного обеспечния
Мы подробно обсуждаем эту ситуацию в документе [Undercollateralization and Liquidation](https://github.com/Estebank97/Keep-Node-Operation/wiki/Manage-your-Nodes#undercollateralization-and-liquidation) .
Основной причиной этой проблемы является волатильность ценового соотношения ETH/BTC, приводящая к снижению относительной цены ETH к BTC. Оповещения должны быть включены для мониторинга этого отношения, чтобы затем вручную добавить ETH для обеспечения.

Мы ожидаем, что это станет существенной проблемой, и следует включить дополнительную автоматизацию, доступную в Keep Dashboard. Например, обеспечить резервный залог, который можно использовать по мере необходимости. По состоянию на август 2020 года никаких планов по этой функциональности не существует.


## Высокая доступность
### Общие соображения о Keep Team
Команда Keep написала подробный документ, в котором рассматриваются многие аспекты запуска [Keep ECDSA ноды (англ.)](https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc#run-ecdsa-keep) с высокой доступностью.

>Keep Network ожидает определенных результатов для каждой ноды, работающей в сети. Чтобы помочь достичь этих результатов рассмотрим следующие критерии:
>
>* Важно держать ноды онлайн. Мы настоятельно рекомендуем стабильное и резервное подключение к интернету.
>
>* Подключение к ноде Ethereum производственного уровня на собственном хостинге.
>
>* Постоянное и резервное хранилище, которое выдержит замену виртуальной машины, а также отказ диска.
>
>* Каждый Keep ECDSA клиент, работающий в сети, требует наличия уникальной учетной записи оператора Ethereum.
>
>* Каждый Keep ECDSA клиент, работающий в сети, требует уникального IP-адреса или уникального порта приложения, работающего под тем же IP-адресом.



### Размещение на базе Kubernetes 
Гарантировать высокую доступность в Keep Production System путём введения резервных нод, путём размещения на базе [Kubernetes](https://kubernetes.io/). 
[Kubernetes Deployment Section (англ.)](https://github.com/Estebank97/Keep-Node-Operation/wiki/Deploy-your-Node#kubernetes-installation-guide-for-ecdsa-nodeode) - инструкция по установке.

Детализированый документ от команды Keep Team с информацией о ECDSA Node  [Run ECDSA Keep (англ.)](https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc#5-deployment-consideration)

---
`Источник из официальной документации Keep Team, отредактированный и дополненный сообществом. '[Источник] (https://keep-network.gitbook.io/staking-documentation/)`

`Авторы: Ramaruro, EstebanK`
`Перевод: ingag`

