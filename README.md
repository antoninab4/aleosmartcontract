# aleo

## Создаем кошелек Aleo https://aleo.tools/

### Запрашиваем тестовые токены в твиттере

`@AleoFaucet send 10 credits to $YOUR_WALLET_ADDRESS` 
где $YOUR_WALLET_ADDRESS ваш адрес кошелька алео

#   Устанавливаем SnarkOS

`sudo apt-get update`

`sudo apt-get upgrade`

`sudo apt-get install`

`screen -S anasayfa`

`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

`git clone https://github.com/AleoHQ/snarkOS.git --depth 1`

`cd snarkOS`

`./build_ubuntu.sh`

`source $HOME/.cargo/env`

`cargo install --path .`


# Настраиваем язык Leo

`cd`

`git clone https://github.com/AleoHQ/leo`

`cd leo`

`cargo install --path .`

`leo`

# Разворачиваем тестовое приложение

`cd $HOME`

`mkdir demo_deploy_Leo_app && cd demo_deploy_Leo_app`

Далее вставляем адрес вашего кошелька

`WALLETADDRESS="ваш адрес кошелька"`

`APPNAME=любое-словона-англ-языке_"${WALLETADDRESS:4:6}"`

`echo $APPNAME`

`leo new "${APPNAME}"`

`cd "${APPNAME}" && leo run && cd -`

`PATHTOAPP=$(realpath -q $APPNAME)`

`echo $PATHTOAPP`

`cd $PATHTOAPP && cd ..`

Далее вставляем приватку от кошелька

PRIVATEKEY=""
Далее вставляем данные полученные из Record на сайте https://aleo.tools/

RECORD=""
!!!!!!!!!!!!!!!!! Последняя команда ее выполняйте как я показал на видео

snarkos developer deploy "${APPNAME}.aleo" --private-key "${PRIVATEKEY}" --query "https://vm.aleo.org/api" --path "./${APPNAME}/build/" --broadcast "https://vm.aleo.org/api/testnet3/transaction/broadcast" --fee 600000 --record "${RECORD}"
