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
* 669 drain transactions (some wallets were not fully emptied from the first attempt)
* Total amount of stolen coins 97.05 SOL (around $20,000)

## The material of investigation
* Downloaded and uploaded into PostgreSQL transaction history of 655 compromised wallets (3,782,452 transaction records in the table `transaction_data`)
* Manual table `address_solname` contains Solana public names of most used addresses by compromised wallets
![](images/address_solname.png)
* The full backup of database with 2 tables can be downloaded [here](TBD)

## Conclusions
* Private keys of victim wallets were compromised somehow, and there are direct transfers from wallet to wallet
* *The best idea is to move tokens from compromised wallets.*
* Check if your Solana wallet was compromised. Here the full list of victims. [Compromised wallets](compromised_wallets.txt)

The investigation is still underway...

>> [Other investigations by @cryptokarl013](https://cryptokarl013.github.io/)

