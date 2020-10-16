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
**First of all: make sure that you are running the latest versions of clients with the latest contracts. Having connected peers + infura queries is the key to success.**

You can check the logs for each node with these commands :`docker logs *node-name*`
You can find your nodes name with the `docker ps` command (last column -> names)
You can also see some other common ways of getting specific information from the logs with [here](https://github.com/Estebank97/Keep-Node-Operation/wiki/Manage-your-Nodes#ecdsa-node-maintenance)

If you see connected peers you should be fine:

<p align="center">
  <img width="719" alt="Intro" src="https://user-images.githubusercontent.com/68087535/89208516-e7419d80-d592-11ea-9822-13be0ae02cb1.png">
</p>

In this example are [27] connected peers.


## Common Errors and Warnings
If you have connected peers then your node is up and running.

On the other side, if you see CRITICAL or some WARNING messages, then maybe your node is not working properly.
Let’s see some common examples and point in the right direction to solve them :

### Just ignore these WARNINGS

<p align="center">
  <img width="719" alt="Ignore" src="https://user-images.githubusercontent.com/68087535/89208525-ec9ee800-d592-11ea-8836-ac5276be14b9.png">
</p>
Connection to some specific peer couldn’t be established, shouldn’t be a problem….as you can see you’re connected 71 peers, so it’s ok !

### Config.toml File errors
Check your config.toml file on your node’s folder, some sort of grammar error, something misspelled:
<p align="center">
  <img width="719" alt="config" src="https://user-images.githubusercontent.com/68087535/89208529-ee68ab80-d592-11ea-944e-c6538db35110.png">
</p>


Check that you set the password correctly, as in `export KEEP_CLIENT_ETHEREUM_PASSWORD="your_eth_wallet_password"` :
<p align="center">
  <img width="719" alt="pass1" src="https://user-images.githubusercontent.com/68087535/89208536-f1fc3280-d592-11ea-9977-0d9bb22dfc9a.png">
</p>



This shows contracts which are defined in the Config.toml file. Make sure you’ve got the latest updates. (You can double check on the pinned messages in the discord channel or in Github (https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc) :

<p align="center">
  <img width="719" alt="contract1" src="https://user-images.githubusercontent.com/68087535/89208553-f4f72300-d592-11ea-8784-0e055f75ed6b.png">
</p>

### Errors after updating addresses inside Config.toml 
From time to time performing some updates on the node is necessary, e.g. when Keep Team updates Contract addresses :
<p align="center">
  <img width="750" alt="contract2" src="https://user-images.githubusercontent.com/68087535/89208558-f6285000-d592-11ea-942b-a22477b3b5f1.png">
</p>
In this example the addresses where changed at the wrong spot inside Config.toml.


### Errors from Token Delegation / Contracts authorization
<p align="center">
  <img width="719" alt="Autho" src="https://user-images.githubusercontent.com/68087535/89208564-f7597d00-d592-11ea-8c88-ec94438bb1d5.png">
</p>
Self explanatory, you have to go to the Keep Token app, and check if token delegation or contracts authorization is missing.



## Other Warnings
<p align="center">
  <img width="719" alt="Other 1" src="https://user-images.githubusercontent.com/68087535/89208567-f7f21380-d592-11ea-9c87-71cd7227bf5f.png">
</p>
Some sort of problem with Keep Contracts on-chain, nothing you can do about it.

<p align="center">
  <img width="719" alt="Other 2" src="https://user-images.githubusercontent.com/68087535/89208572-f9bbd700-d592-11ea-86ed-409db54acde8.png">
</p>
Problem is on-chain, something to do with trying to join the bonded sortition pool.



!> @Nico186 made this excelent [document](https://docs.google.com/document/u/2/d/e/2PACX-1vRYtVyLSwuNBL9Xk-M1HeHloJ7MIGqwiEzsuXYnKHQqnSz2gfd2Q3czJeOzEferPKIr7GvIznQxsckb/pub) about interpreting KEEP Error and Warning Logs.

---
`Источник из официальной документации Keep Team, отредактированный и дополненный сообществом. '[Источник] (https://keep-network.gitbook.io/staking-documentation/)`

`Авторы: Ramaruro, EstebanK`
`Перевод: tony__s_h`
