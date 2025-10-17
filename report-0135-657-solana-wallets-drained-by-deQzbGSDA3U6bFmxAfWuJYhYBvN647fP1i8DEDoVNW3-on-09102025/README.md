# Crypto Report #0135 657 solana wallets were drained by deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3 within one day on October 9, 2025

## Keywords
crypto theft, Solana, pump.fun

## Abstract
On October 9, 2025 657 wallets were fully drained and all SOL coins were transferred to `deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`

![](images/victim1.png)
![](images/victim2.png)
![](images/victim3.png)
![](images/victim4.png)
![](images/victim5.png)

## Details of the attack:
* 657 Solana wallets were drained from Oct 09, 2025 00:00  till Oct 09, 2025 17:40 (17 hours attack)
* Only SOL coins were drained and transferred to the Solana wallet [deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3](https://solscan.io/account/deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3)
* 669 drain transfers
* Total amount of stolen coins 97.05 SOL (around $20,000)

## The material of investigation
* Downloaded and uploaded into PostgreSQL transaction history of 655 compromised wallets (3,782,452 transaction records in the table `transaction_data`)
* Manual table `address_solname` contains Solana public names of most used addresses by compromised wallets
![](images/address_solname.png)
* The full backup of the analytics PostgreSQL database can be downloaded [here](TBD) for your own investigation

## Analytics
### Stats
* average amount per compromised walllet is 33$, the max is #1,077.98
![](images/top_victims.png)
  
### The attack was planned and started at midnight, the scenario of the attack is the same: 
* calling closeAccount function  to return all available rent SOL to the main victim wallet
* drain all SOL coins and transfer them to a malicious wallet `deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`
* remained SOL amount to <1$ on compromised accounts
* 12 of 657 accounts where drained twice to drain remained SOL coins
 <code>select count(*), from_address from transaction_data where to_address = 'deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3' and root != 'deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3' group by from_address order by count(*) desc<code>
![](images/drained_twice.png)




## Conclusions
* Private keys of victim wallets were compromised somehow, and there are direct transfers from wallet to wallet
* *The best idea is to move tokens from compromised wallets.*
* Check if your Solana wallet was compromised. Here the full list of victims. [Compromised wallets](compromised_wallets.txt)

The investigation is still underway...

> [Other investigations by @cryptokarl013](https://cryptokarl013.github.io/)

