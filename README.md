
Para gerar uma imagem NFT utilizando o nft-generator-py:
scss
Copy code
from nft_generator_py import NFTGenerator

generator = NFTGenerator()
generator.generate_image()
Para carregar uma chave privada do Ocean Protocol utilizando o ocean.py:
java
Copy code
from ocean_lib.web3_internal.wallet import Wallet

private_key = "..."
wallet = Wallet(private_key)
Para listar todos os ativos disponíveis no mercado do Ocean Protocol utilizando o ocean.py:
scss
Copy code
from ocean_lib.models.asset_list import AssetList

asset_list = AssetList()
assets = asset_list.list()
Para instanciar um modelo GPT-3 do OpenAI utilizando o GPT3Discord:
java
Copy code
from GPT3Discord import GPT3

model = GPT3(api_key="...", model_id="...")
Para enviar uma mensagem para o modelo GPT-3 e obter uma resposta utilizando o GPT3Discord:
makefile
Copy code
response = model.send_message("Olá, tudo bem?")
Para gerar uma imagem NFT personalizada utilizando o nft-generator-py:
scss
Copy code
from nft_generator_py import NFTGenerator

generator = NFTGenerator()
generator.set_color("#FF0000")
generator.set_background_color("#FFFFFF")
generator.set_shape("circle")
generator.set_text("Hello World!")
generator.generate_image()
Para obter informações sobre um ativo específico utilizando o ocean.py:
makefile
Copy code
from ocean_lib.models.data_token import DataToken

asset_address = "..."
token = DataToken(asset_address)
info = token.info()
Para listar todos os provedores de armazenamento disponíveis no Ocean Protocol utilizando o ocean.py:
java
Copy code
from ocean_lib.ocean.util import get_provider_info

providers = get_provider_info()
Para treinar um modelo GPT-3 do OpenAI utilizando o GPT3Discord:
css
Copy code
model.train(prompt="Olá, tudo bem?", examples=["Sim, estou bem", "Não estou bem"])
Para transferir um ativo do Ocean Protocol utilizando o ocean.py:
makefile
Copy code
from ocean_lib.models.data_token import DataToken

asset_address = "..."
to_address = "..."
amount = 1

token = DataToken(asset_address)
token.transfer(to_address, amount)
Para obter o preço atual de um ativo no mercado do Ocean Protocol utilizando o ocean.py:
makefile
Copy code
from ocean_lib.models.bpool import BPool

asset_address = "..."
pool = BPool(asset_address)
price = pool.get_price()
Para listar todas as transações de um ativo específico utilizando o ocean.py:
makefile
Copy code
from ocean_lib.models.data_token import DataToken

asset_address = "..."
token = DataToken(asset_address)
transactions = token.get_transactions()
Para gerar uma imagem NFT aleatória utilizando o nft-generator-py:
scss
Copy code
from nft_generator_py import NFTGenerator

generator = NFTGenerator()
generator.set_random_properties()
generator.generate_image()
Para criar um novo ativo no Ocean Protocol utilizando o ocean.py:
makefile
Copy code
from ocean_lib.models.data_token import DataToken

name = "My Asset"
symbol = "MYASSET"
initial_supply = 1000

token = DataToken()
token.create(name, symbol, initial_supply)
Para obter a lista de todas as contas disponíveis no Ocean Protocol utilizando o ocean.py:
java
Copy code
from ocean_lib.ocean.util import get_account_addresses

accounts = get_account_addresses()





<!--
Copyright 2023 Ocean Protocol Foundation
SPDX-License-Identifier: Apache-2.0
-->

<h1 align="center">
<img src="https://github.com/oceanprotocol/art/blob/main/splashes/ocean_py.png?raw=true" width="300"/>
</h1>

> ocean.py: a Python library to privately & securely publish, exchange, and consume data.

[![Maintainability](https://api.codeclimate.com/v1/badges/a0be65f412a35440c63e/maintainability)](https://codeclimate.com/github/oceanprotocol/ocean.py/maintainability)
[![Test Coverage](https://api.codeclimate.com/v1/badges/a0be65f412a35440c63e/test_coverage)](https://codeclimate.com/github/oceanprotocol/ocean.py/test_coverage)

With ocean.py, you can:

- **Publish** data services: downloadable files or compute-to-data. Create an ERC721 **data NFT** for each service, and ERC20 **datatoken** for access (1.0 datatokens to access).
- **Sell** datatokens via for a fixed price. Sell data NFTs.
- **Transfer** data NFTs & datatokens to another owner, and **all other ERC721 & ERC20 actions** using [web3.py](https://web3py.readthedocs.io) or [Brownie](https://eth-brownie.readthedocs.io/en/latest/).

ocean.py is part of the [Ocean Protocol](https://www.oceanprotocol.com) toolset.

This is in beta state. If you run into problems, please open up a [new issue](/issues).

- [🏄 Quickstart](#-quickstart)
- [🦑 Development](#-development)
- [🏛 License](#-license)

## 🏄 Quickstart

Follow these steps in sequence to ramp into Ocean.

 1. **[Install Ocean](READMEs/install.md)**
 2. **Setup:**
    - **[Remote](READMEs/setup-remote.md)** (Win, MacOS, Linux)
    - *or* **[Local](READMEs/setup-local.md)** (Linux only)
 3. **[Walk through main flow](READMEs/main-flow.md)**: publish asset, post for free / for sale, dispense it / buy it, and consume it

### Tools

- [Define gas strategy](READMEs/gas-strategy-remote.md) - auto-determine gas fee for remote networks
- [Search & filter data](READMEs/search-and-filter-assets.md) - find assets by tag
- [Custody-light flow](READMEs/custody-light-flow.md) - consume a free & a priced asset without custody

### Use-case flows

- [Predict ETH](https://github.com/oceanprotocol/predict-eth) - data challenges with prize $$ to predict future ETH price
- [Data Farming](READMEs/df.md) - curate data assets, earn rewards

### On-chain key-value store via data NFTs

- [Sharing public data on-chain](READMEs/key-value-public.md) - e.g. public AI models
- [Sharing private data on-chain](READMEs/key-value-private.md) - e.g. private AI models

### More types of data assets

Each of the following shows how to publish & consume a particular type of data.
- [C2D](READMEs/c2d-flow.md) - tokenize & monetize AI algorithms via Compute-to-Data
- [REST API](READMEs/publish-flow-restapi.md) - Example on Binance ETH price feed
- [GraphQL](READMEs/publish-flow-graphql.md) - Example on Ocean Data NFTs
- [On-chain data](READMEs/publish-flow-onchain.md) - Example on Ocean swap fees

### Learn more
- [Understand config parameters](READMEs/parameters.md) - envvars vs files
- [Learn about off-chain services](READMEs/services.md) - Ocean Provider for data services, Aquarius metadata store

## 🦑 Development

- **[Developers flow](READMEs/developers.md)** - to further develop ocean.py
- [Release process](READMEs/release-process.md) - to do a new release of ocean.py

## 🏛 License

    Copyright ((C)) 2022 Ocean Protocol Foundation

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

