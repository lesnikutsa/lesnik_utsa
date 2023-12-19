# Autonity challenge Go with the flow
https://game.autonity.org/round-4/on-chain-tasks/transact-flow/

Aim for at least 1000 cross-wallet ATN transactions per epoch. In this case, the amount received must be at least 180 ATN per epoch. Since 1 epoch is half an hour, we need to make more than 1000 transactions in half an hour
Since changing the “nonce” has a time delay, with normal sending of transactions from the account we can reach a threshold of approximately 950 transactions in half an hour. Therefore, in our script we will automatically change this parameter

## Instructions:
To complete this task, make sure that you have installed the autonity node, the ```aut``` tool and replenished your wallet balance with the required number of coins
Use the script below to perform transactions, after replacing the values below with your own

**WALLET_TO_RECEIVE** - wallet to which coins will be sent

**PASSWORD** - password from the wallet from which coins will be sent

**1** - nonce value indicating the current value of sent transactions from your account. You can find out using the command ```aut account info``` in **"tx_count"**

```bash
#!/bin/bash
for ((c=1;c<=999999999;c++))
do

sleep 0.1; aut tx make --to WALLET_TO_RECEIVE --value 1 -n "$c" | aut tx sign -p 'PASSWORD' - | aut tx send - >> /root/t1.log
done
```
## Possible problems and inconveniences:
- Nonce value stuck and transactions blocked. Apparently this is possible due to the mempool being full. It was cured by manually sending any transaction and restarting the script
- When the script is running, it will not be possible to send regular transactions. Pause it temporarily before sending a regular transaction
- Sometimes there may be errors in the node logs due to the fact that the transaction does not have time to send. You can play around with the value of ```sleep```
- In some cases, there was a noticeable problem with a lack of gas for transactions. In this case, add the ```-F 0.000001``` flag to the send command

---

# RU

Стремитесь получить не менее 1000 транзакций ATN между кошельками за эпоху. При этом полученная сумма должна составлять не менее 180 ATN за эпоху. Так как 1 эпоха составляет пол часа, то нам необходимо сделать больше 1000 транзакций за пол часа
Так как изменение "nonce" имее временную задержку, то при обычной отправке транзакций с аккаунта мы можем достичь порога примерно 950 транзакций за пол часа. Поэтому в нашем скрипте мы будем автоматически изенять данный параметр

## Инструкции:
Для выполнения данной задачи убедитесь, что Вы установили ноду autonity, инструмент aut и пополнили баланс своего кошелька необходимым количеством монет
Используйте скрипт ниже для выполнения транзакций

**WALLET TO RECEIVE** - кошелек, на который будут отправлены монеты

**PASSWORD** - пароль от кошелька, с которого будут отправлены монеты

**1** - значение nonce, означающее текущее значение отправленных транзакций с Вашей учетной записи. Можно узнать с помощью команды ```aut account info``` в **"tx_count"**

```bash
#!/bin/bash
for ((c=1;c<=999999999;c++))
do

sleep 0.1; aut tx make --to WALLET_TO_RECEIVE --value 1 -n "$c" | aut tx sign -p 'PASSWORD' - | aut tx send - >> /root/t1.log
done
```

## Возможные проблемы и неудобства:
- Зависание значения nonce и блокирование транзакций. По всей видимости такоей возможно из-за переполнения мемпула. Было вылечено ручной отправкой любой транзакции и перезапуска скрипта
- При работе скрипта не получится отправлять обычные транзакции. Временно приостановите его работу перед отправкой обычной транзакции
- Иногда в логах ноды могут быть ошибки из-за того, что транзакция не успевает отправиться. Вы можете поиграться со значением ```sleep```
- В некоторых случаях была заметна проблема с нехваткой газа для транзакций. В этом случае добавьте флаг ```-F 0.000001``` в команду отправки

Русскоязычная группа по autonity - https://t.me/autonity_ru
