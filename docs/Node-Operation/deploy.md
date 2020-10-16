# Запуск ваших нод

В этом разделе собраны руководства и подходы, разработанные различными участниками сообщества Keep для облегчения запуска Keep Random Beacon и Keep ECDSA.

**Содержимое этого раздела**
- Установка ноды
- Официальные соображения Keep Network о Random Beacon ноде
- Гайд для абсолютных новичков
- Прочие гайды
- ECDSA нода на Amazon
- Гайды по скриптам
- Kubernetes гайд для ECDSA ноды
- Keep на Windows


# Устновка ноды

Вы можете поддерживать Keep Network, участвовать и получать вознаграждения, управляя следующими нодами:
   * Random Beacon
   * ECDSA

Прямо сейчас Keep Network и система tBTC работает в тестовой сети Ropsten.
Есть несколько очень хороших руководств, которые помогут вам в процессе запуска обоих нод.
Главные шаги установки:
- Создайте на [Infura](https://infura.io/) аккаунт.
- Создайте Ethereum кошелёк, используйте "My Ether Wallet with a keystore" и импортируйте в Metamask.
- Авторизуйте контракты в Keep Dashboard (сейчас тестовая сеть, позже основная сеть), получите несколько KEEP и ETH тестовой сети и делегируйте ETH с помощью Dashboard.
- Используйте VPS (Amazon, Google Cloud, Azure, Vultr, Digital Ocean, Linode, или любой другой), работающий на Ubuntu, установите Docker.
- Запустите Keep ноды.


?> [Keep Tools Guide](https://keeptools.org/) позволяет сгенерировать некоторые файлы, необходимые для запуска, и включает некоторые [Docker команды](https://keeptools.org/docker-commands).

## Официальные соображения Keep Network о Random Beacon ноде
Вы можете найти официальную документацию **Запуск Random Beacon** в Keep Network [здесь] (https://docs.keep.network/run-random-beacon.html).
Это техническое объяснение запуска ноды, но оно не предназначено для новичков. 
> Keep Network требует опеределнного обеспечения для каждой ноды, работающей в сети.

> - Крайне важно, чтобы ноды Keep оставались доступными для Keep Network. Мы настоятельно рекомендуем стабильное и резервное подключение к Интернету.
> - Подключайтесь на собственном хостинге или VPS.
> - Основное и резервное хранилище, которое выдержит ротацию виртуальной машины, а также отказ диска.
> - Каждый Random Beacon, работающий в сети, требует уникальной учетной записи оператора Ethereum.
> - Каждому Random Beacon, работающему в сети, требуется уникальный IP-адрес или уникальный порт приложения, работающий под тем же IP.


## Гайд для абсолютных новичков

- **Nick Grego's** [Step-by-step guide for installing both ECDSA & Beacon Keep Network nodes on VPS with 100$ voucher](https://medium.com/@nickgrego/step-by-step-guide-for-installing-both-ecdsa-beacon-nodes-on-vps-with-100-voucher-db930ab2a667)
> Это пошаговое руководство для новичков по запуску своих первых нод в Keep Network с полностью бесплатным сервером VPS и с минимальным использованием командной строки. 

Nick's гайд (Gregory#6997 в Discord) сделал скриншоты для каждого шага и примеры логов, где вы можете убедиться, что все работает нормально.

- **Ben Longstaff's** [A beginners quick start guide to staking on the Keep Network testnet using DigitalOcean](https://medium.com/@ben_longstaff/a-beginners-quick-start-guide-to-staking-on-the-keep-network-testnet-using-digitalocean-5a74ca60adc3)

Другое известное руководство для начинающих, также с легкими для понимания скриншотами, объясняющими каждый шаг.

- **JackRemix'** [The absolute beginner’s guide to Playing for Keeps](https://medium.com/@jack.baldwin/the-absolute-beginners-guide-to-playing-for-keeps-aea9ab32f6e8) **действительно впечатляет** 

## Прочие гайды

- **Alex Novy's** [Run Random Beacon in KEEP Network Testnet](https://medium.com/@novysf/run-a-keep-network-testnet-node-37096946af35)

Для этого руководства вы уже должны иметь VPS.

- **Chris Projecttent's** [Deploy a Random Beacon Node on the Keep Testnet](https://medium.com/@projecttent/deploy-a-random-beacon-node-on-the-keep-testnet-6c95d742fa5a) and [Deploy a Keep ECDSA Node on the Keep Testnet](https://medium.com/@projecttent/deploy-a-keep-ecdsa-node-on-the-keep-testnet-13f374b0c11a).

Требования к оборудованию немного выше, чем у других, но, с другой стороны, вам не нужна учетная запись Infura.

- **Afmsavage's** [Keep Ecdsa Node](https://gist.github.com/afmsavage/8fc19937a6b263f05c3e215d8860629c).

Pantsme#2124, из Discord, разработал это руководство как пошаговое руководство по запуску ноды Keep-ECDSA для основной или тестовой сети, что очень удобно для выявления основных различий между обоими развертываниями.

- **Papyasha's** [Deploy Edcsa and Random Beacon Nodes](https://gist.github.com/papyasha/49925cf882545dada27b3f3fb7f48304).

Предполагается, что у вас уже выполнена подготовительная работа, то есть VPS под управлением Linux, Infura, Wallet и другие предварительные шаги.

## ECDSA нода на Amazon

- **Afmsavage's** [KEEP-ECDSA Node Terraform for AWS](https://github.com/afmsavage/keep-ecdsa-tf/tree/testnet). Проходит через настройку Amazon, которая включает встроенные электронные уведомления о статусе вашей ноды.

## Гайды по скриптам
Скрипты помогают автоматизировать пошаговый процесс настройки ноды ECDSA на сервере.

- **Jeremyid's** [Easy Keep Nodes](https://github.com/jeremyid/easy-keep-nodes). Experience#2376 сделал действительно простые скрипты для обоих нод.

- **Crypto Enthu's** [Keep Network — ECDSA Node Setup Guide](https://medium.com/@cryptoenthu1/keep-network-ecdsa-node-setup-5164b7c2cec3) и его [репозиторий](https://github.com/cryptoenthu1/keep-ecdsa-repo) Naga#0916.

- **Finally-get-it's** Скрипты для [Random Beacon](https://github.com/finally-get-it/keep-rb-repo) и [Edcsa Node](https://github.com/finally-get-it/keep-ecdsa-repo) от Ingag#8096. Эти руководства/репозитории основаны на руководстве Crypto Enthu, что позволяет изменять имя проекта и порты.

- **DaniellMesquita's** [Keep Bot Node Installation Script](https://github.com/DaniellMesquita/keepbot), как он говорит: Абсурдно простой скрипт для настройки вашей сети KEEP и нод tBTC.

## Kubernetes гайд для ECDSA ноды
Запуск в кластере Kubernetes обеспечивает резервность для повышения надежности. Если нода выходит из строя - на её место запускается резервная копия.
Алекс Кроу написал это отличное руководство по запуску ноды ECDSA в Kubernetes, включая [Helm Charts] (https://github.com/ajcrowe/keep-helm-chart) и мониторинг с помощью Prometheus & Grafana.
[Deploy a KEEP Node to Kubernetes and Monitor with Prometheus & Grafana](https://medium.com/@alex.j.crowe/deploy-a-keep-node-to-kubernetes-and-monitor-with-prometheus-grafana-4ee5c7d9e9a4)


## Видео

-**Bakarapara's** [Video walkthrough of Alex Novy's Guide](https://youtu.be/7zgXxqnYF_0). Нет звука, все изображения. Легко понять.

## Keep на Windows

- [Running an ECDSA Keep locally hosted, testnet node on Windows for noobs](https://docs.google.com/document/d/1hsI8AtUiGAfcHxik-3akSRjysC0Zw0CVmHxmbNtZyHI/edit#). Некоторые данные (контракты и пиры) могут быть устаревшими. Но полезно, если вы хотите провести несколько тестов на компьютере.

`Источник из официальной документации Keep Team, отредактированный и дополненный сообществом. '[Источник] (https://keep-network.gitbook.io/staking-documentation/)`

`Авторы: Ramaruro, EstebanK`
`Перевод: tony__s_h`


