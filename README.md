# rpi-ec

This repository includes instructions for installing the [Electron Cash](https://electroncash.org/) wallet with [CashFusion](https://cashfusion.org/), on a Raspberry Pi 400 running Ubuntu Linux. Electron Cash is a full-features HD wallet for Bitcoin Cash (BCH). CashFusion is a [CoinJoin protocol](https://en.bitcoin.it/wiki/CoinJoin) for anonymizing BCH and reclaiming [fugability](https://www.investopedia.com/terms/f/fungibility.asp).

The instructions in this document will walk through the step-by-step commands for installing Electron Cash on a Pi 400 or Raspberry Pi 4 running Ubuntu Linux. The software must be installed from source code, because these devices run a `arm64` architecture which is not included in the AppImage releases for Electron cash.

## Environment

These instructions were last tested on the following hardware and software:

- Pi 400 with 4GB
- Ubuntu 21.10
- EC version [4.2.6](https://github.com/Electron-Cash/Electron-Cash/releases/tag/4.2.6)

## Installation Instructions

Clone the EC Github repository and enter it.

- `git clone https://github.com/Electron-Cash/Electron-Cash`
- `cd Electron-Cash`
- `git checkout 4.2.6`

Install Python and pip.

- `sudo apt update`
- `sudo apt install python3-pip -y`

Install core dependencies.

- `sudo python3 setup.py install`

Install other dependencies.

- `sudo apt install -y python3-pyqt5 python3-socks python3-pyqt5.qtsvg`
- `pip3 install google-api-python-client`
- `pip3 install jsonrpc`
- `pip3 install jsonrpclib`

Install dependencies from EC README:

- `pip3 install -r contrib/requirements/requirements.txt --user`

Create translations

- `./contrib/make_locale`

Compile libsecp256k1

- `./contrib/make_secp`

Install Tor. This is needed for CashFusion.

- `sudo apt install tor -y`
