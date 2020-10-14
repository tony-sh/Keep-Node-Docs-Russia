# Введение в tBTC & Keep Network 


## DeFi
Децентрализованные финансы (DeFi) это система открытых и взаиосвязанных финансовых услуг и продуктов, созданных и работающих в сети Ethereum. К июлю 2020, почти 4 миллиарда долларов задействованы во всех приложениях DeFi, предлагающих займы, токены, деривативы, обмены через децентрализованные смарт-контракты.  Этот объём продолжает расти.

Протоколы DeFi имеют модульную структуру, позволяющую им взаимодействовать друг с другом, создавая все более сложную систему.  Поскольку DeFi продукты - это код, который находится в сети блокчейн, такой как Эфириум(Ethereum), они никогда не смогут быть отключены или скрыты от тех, кот хочет ими воспользоваться. Таки образом, любой, кто имеет доступ в интернет, может пользоваться услугами кредитования, комплексными финансовыми продуктами,  сбережениями, инвестиционными и трейдинговыми возможностями на DeFi.

## Намерения tBTC
Несмотря на экспоненциальный рост проектов в DeFi и Эфириум, на биткоин всё-ещё приходится две трети общего объёма криптовалюты в мире.a

Как Ильяс Хацис представляет tBTC в своем [блоге (англ.)](https://medium.com/@iliashatzis/could-bitcoin-on-defi-displace-banks-yes-4c0ad99f0da4) :
> “Биткоин DeFi мечта биткойнеров. Можем мечта осуществилась и новый tBTC проект принесёт Bitcoin в мир DeFi.
> Биткоин может сильно трансформировать DeFi и это прекрасно понимают в команде Keep.” 

Команда Keep запустила tBTC, децентрализованную, надёжную и застрахованную систему хранения биткоинов в токенах TBTC Ethereum ERC-20, с курсом 1:1 к BTC. Владельцы биткойнов, которые хотят потратить свои BTC на Ethereum и DeFi, не должны доверять хранителям (подписанты), потому что подписывающие стороны должны внести залог, превышающий стоимость BTC, которую они держат на хранении.

?> Превосходное [видео (англ.)](https://www.youtube.com/watch?v=cfmQiArg3B8) об этом от Artem#4718 а Discord.

Подписанты выбираются случайным образом из более крупной сети для подписывающих узлов и работают в группах по три. Залог гарантирует, что поведение подписывающих сторон в системе остается честным, с риском потери их залога в случае мошенничества или недостаточного обеспечения. Если подписывающие стороны переместят средства без разрешения, оставив на хранении больше TBTC, чем BTC, система конфискует их залог, чтобы купить и уничтожить эквивалент TBTC с рынка, в результате чего количество TBTC и BTC на хранении уравновесится.

<p align="center">
  <img width="619" alt="Beacon" src="https://user-images.githubusercontent.com/68087535/88100735-57075f80-cb73-11ea-996f-ec2d9590b073.png">
</p>


## Keep Network

tBTC - это приложение в [Keep Network](https://keep.network), которому Бэн Лонгстафф дал отличное [описание (англ.)](https://medium.com/@ben_longstaff/secure-multi-party-computation-smpc-explained-visually-ecde155fc7c0):

> “Keep Network намеревается стать решением для обеспечения конфиденциальности для безопасного хранения данных вне сети, и при этом значительно расширяет функциональность смарт-контрактов и массовое внедрение технологии блокчейн.”

Keep Network - это решение для обеспечения конфиденциальности, в котором хранятся распределенные небольшие объемы данных, такие как приватный ключ, и поддерживается взаимодействие между цепочками. Keeps - это смарт-контракты, которые позволяют другим смарт-контрактам безопасно взаимодействовать с личными данными. Они построены на ECDSA алгоритме, поддерживаемом многими ведущими блокчейнами, и облегчают подписание децентрализованных групп с помощью многосторонних пороговых подписей.

Keep Network в [Messari](https://messari.io/article/announcement-messari-adds-11-new-disclosures-registry-participants-surpassing-50-members) открытый зарегестрированный участник. Присоединившись к этому реестру, эти проекты взяли на себя обязательство повысить уровень прозрачности криптоактивов за счет постоянного раскрытия информации.

[Keeps Grants Explorer](https://explorer.keep-grants.info/) от MutedTommy#3155 (в Discord) отслеживает распределенные гранты KEEP в токенах.

### t-ECDSA нода

T-ECDSA keep обеспечивает безопасность транзакций с помощью нескольких индивидуальных ключей, хранимых несколькими подписантами. Децентрализованная подпись выполняется с помощью sMPC (безопасное многостороннее вычисление) для вычислений на общих ключах, не раскрывая их. Ответственность за подписи разделена, и требуется определенное количество участников для создания подписи.

В общем, это работает так: смарт-контракт Ethereum просит Keep Network открыть новый t-ECDSA Keep. Это хранилище поддерживается группой случайно выбранных подписантов из кластера sMPC, более крупной сети подписывающих узлов. Эти подписывающие лица используют t-ECDSA для генерации ключа и предоставления подписи. Подписанты могут подписывать все что угодно, включая транзакции блокчейна. Смарт-контракт Ethereum может попросить keep подписать транзакцию на любом блокчейне на основе ECDSA, Биткойн - лишь один из них.

Этот механизм надёжн, так как подписанты независимы; это люди и организации запустившие ноду с sMPC кластером. 

<p align="center">
  <img width="319" alt="Beacon" src="https://user-images.githubusercontent.com/68167410/88845610-05ca2200-d1aa-11ea-9d8b-400516fed25c.png">
</p>

### Random Beacon нода

Random Beacon (случайные маяки) другая составляющая сети: децентрализованный инструмент случайного выбора подписантов способом. Этот маяк - BLSThreshold Relay, им нельзя управлять или манипулировать. Это надежный источник случайности для выбора групп. Никто не знает, кем будут подписывающие лица, включая самих подписывающих лиц, до того момента, пока они не будут выбраны случайным маяком. Это гарантирует, что подписывающие стороны не смогут вступить в сговор с целью кражи средств или атак на сеть, и именно поэтому так важна истинная случайность, предоставляемая маяком. 

**Random Beacon и t-ECDSA Keeps ядро в сети Keep.**



***

**Источники и полезная информация :**
- [Could Bitcoin on DeFi displace banks? Yes](https://medium.com/@iliashatzis/could-bitcoin-on-defi-displace-banks-yes-4c0ad99f0da4) by Ilias Hatzis
- [Bridging Bitcoin and Ethereum](https://blog.keep.network/bridging-bitcoin-and-ethereum-b2f9923630a7) from the Keep Network Blog
- [Secure Multiparty Computation](https://medium.com/@ben_longstaff/secure-multi-party-computation-smpc-explained-visually-ecde155fc7c0) by Ben Longstaff
- [Building Bridges between Blockchains with tECDSA keeps](https://blog.keep.network/building-bridges-between-blockchains-with-t-ecdsa-keeps-e58d6debb8fd) by Piotr Dyraga from the Keep Network Blog
- [Staking Documentation](https://keep-network.gitbook.io/staking-documentation/) from the Keep Network Documentation
- [tBTC Technical Overview](https://tbtc.network/developers/tbtc-technical-system-overview/) from the tBTC Website
- [What's in a beacon](https://blog.keep.network/whats-in-a-beacon-12c34b0bc078) by Antonio Salazar Cardozo from the Keep Network Blog
- [Why is Trusted Randomness So Important?](https://blog.keep.network/why-is-trusted-randomness-so-important-c22de1c1c5ee) by Antonio Salazar Cardozo from the Keep Network Blog
- [Threshold ECDSA — Safer, more private multi-signatures](https://blog.keep.network/threshold-ecdsa-safer-more-private-multi-signatures-51153f3e9ed2) by Antonio Salazar Cardozo from the Keep Network Blog on Keep developer Piotr Dyraga’s presentation on threshold-ECDSA from San Francisco Blockchain Week 2018.
- [Defi explained](https://decrypt.co/resources/defi-decentralized-finance-explained-guide-learn) by Decrypt.co
- [What is Defi](https://defipulse.com/blog/what-is-defi/) by Defipulse
- [Keep promo video](https://www.youtube.com/watch?v=h2IErqf-VrQ) by Lelka Bo in Discord Design Channel
- [TBTC: A New Sidechain Design for Bitcoin](https://insights.deribit.com/market-research/a-new-sidechain-design-for-bitcoin/) by Su Zhu in Deribit Insights
- Images are from SpaceWalker (Discord Design Channel), [Ilias Hatzis](https://medium.com/@iliashatzis) (from his story), Keep Team (Discord Design Channel).

---
`Источник из официальной документации Keep Team, отредактированный и дополненный сообществом. '[Источник] (https://keep-network.gitbook.io/staking-documentation/)`

`Авторы: Ramaruro, EstebanK`
`Перевод: tony__s_h`
