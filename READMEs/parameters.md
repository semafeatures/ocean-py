# On Config Parameters

We can set any config parameter (a) via an envvar, or (b) via a config file. Envvar values override config file values.

An `Ocean` instance will hold a `Config` instance that holds various config parameters. These parameters need to get set. This is set based on what's input to `Ocean` constructor:

1. dict input: ```Ocean({'network':..})```
1. Config object input: ```Ocean(Config('config.ini'))```
1. no input, so it uses CONFIG_FILE envvar

Here are examples.

## 1. dict input, filled from envvars

First, in console:
```console
export NETWORK_URL=https://rinkeby.infura.io/v3/<your Infura project id>
export AQUARIUS_URL=https://aquarius.rinkeby.v3.dev-ocean.com
export PROVIDER_URL=https://provider.rinkeby.v3.dev-ocean.com
```

Then, do the following in Python. The `Ocean` constructor takes a `dict`, which in turn is set by envvars.
```python
import os
from ocean_lib.ocean.ocean import Ocean
d = {
   'network' : os.getenv('NETWORK_URL'),
   'metadataStoreUri' : os.getenv('AQUARIUS_URL'),
   'providerUri' : os.getenv('PROVIDER_URL'),
}
ocean = Ocean(d)
```

## 1a. Unsetting envvars

Recall that parameters set by envvars override config file values. So, to use a config value in a file, we must remove its envvar.

Here's how. In the console:
```
unset NETWORK_URL AQUARIUS_URL PROVIDER_URL
```

## 2. Config object input, filled from config file

First, in your working directory, create `config.ini` file and fill as follows:
```
[eth-network]
network = https://rinkeby.infura.io/v3/<your infura project id>

[resources]
aquarius.url = https://provider.rinkeby.v3.dev-ocean.com
provider.url = https://aquarius.rinkeby.v3.dev-ocean.com
```

Then, in Python:

```python
from ocean_lib.config import Config
from ocean_lib.ocean.ocean import Ocean
c = Config('config.ini')
ocean = Ocean(c)
```

## 3. No input, so it uses CONFIG_FILE envvar

We'll use the `config.ini` file created from the previous example.

Then, set an envvar for the config file. In the console:
```console
export CONFIG_FILE=config.ini
```

Then, in Python:
```python
from ocean_lib.ocean.ocean import Ocean
ocean = Ocean()
```

## Further details

The file [config.py](https://github.com/oceanprotocol/ocean.py/blob/master/ocean_lib/config.py) lists all the config parameters.

For the most precise description of config parameter logic, see the [Ocean() constructor implementation](https://github.com/oceanprotocol/ocean.py/blob/master/ocean_lib/ocean/ocean.py).