# 3-oji užduotis: „Bitcoin Core“ programinės sąsajos naudojimas - `python-bitcoinlib`

Šiai užduočiai atlikti būtina turėti prieigą prie pilno Bitcoin mazgo (angl. Bitcoin full node). Atsižvelgiant į [didelius  vietos kietąjame diske reikalavimus](https://www.blockchain.com/charts/blocks-size?timespan=all), o taip pat ir Universiteto griežtą saugumo politiką, __rekomenduojame__ įsidiegti [Bitcoin Core realizaciją](https://github.com/bitcoin/bitcoin) pasinaudojant NEMOKAMOMIS debesų technologijos tiekėjo (Gooogle Cloud, AWS ir pan.) paslaugomis. Įdiegimo instrukcijos skirtingoms OS rasite čia: [Unix](https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md), [OS X](https://github.com/bitcoin/bitcoin/blob/master/doc/build-osx.md), [Windows](https://github.com/bitcoin/bitcoin/blob/master/doc/build-windows.md)

- P.S. Už kiekvieną "pritrauktą" kolegą, t.y., tą kuris naudosis Jūsų Bitcoin full-nod'u, gausite po 0.1 papildomo balo! :smile:

- Taip pat reikia įdiegti [python-bitcoinlib](https://pypi.org/project/bitcoinlib/) biblioteką: `pip instal bitcoinlib`.

**Kaip alternatyva, naudokitės jau sukonfigūruotu pilnaverčiu Bitcoin mazgu, prie kurio priėjimas Jums buvo suteiktas**: [https://bitnodes.earn.com/nodes/158.129.140.201-8333](https://bitnodes.earn.com/nodes/158.129.140.201-8333)

## "Apšilimui"

Pirmiausia pabandykite pasileisti ir pasinagrinėti `python-bitcoinlib` bibliotekos panaudojimo pavyzdžius, paimtus iš *Mastering Bitcoin* knygos:

1. **Pavyzdys**: `getblockchaininfo` komandos panaudojimas **python** aplinkoje (terminale ją iškviečiame `bitcoin-cli getblockchaininfo`), kurių pagalba sužinoma ***bitcoin-core*** mazge esančių blokų skaičius, kuris ir yra išvedamas ekrane:

```python
# `rpc_example.py` example
from bitcoin.rpc import RawProxy

# Create a connection to local Bitcoin Core node
p = RawProxy()

# Run the getblockchaininfo command, store the resulting data in info
info = p.getblockchaininfo()

# Retrieve the 'blocks' element from the info
print(info['blocks'])
```

2. **Pavyzdys**: `getrawtransaction` ir `decoderawtransaction` komandų panaudojimas **python** aplinkoje, kurių pagalba yra išvedamos tam tikrų konkrečios (**Alice's**) transakcijos laukų reikšmės ekrane:

```python
# `pc_transaction.py` example
from bitcoin.rpc import RawProxy

p = RawProxy()

# Alice's transaction ID
txid = "0627052b6f28912f2703066a912ea577f2ce4da4caa5a5fbd8a57286c345c2f2"

# First, retrieve the raw transaction in hex
raw_tx = p.getrawtransaction(txid)

# Decode the transaction hex into a JSON object
decoded_tx = p.decoderawtransaction(raw_tx)

# Retrieve each of the outputs from the transaction
for output in decoded_tx['vout']:
    print(output['scriptPubKey']['addresses'], output['value'])
```

3. `getblockhash`, `getblock` komandų panaudojimas **python** aplinkoje, kurių pagalba yra suskaičiuojama visų konkretaus bloko (#**277316**) transakcijų pervedimų (*output*'ų) sumą, į kurią įeina ir *reward*'as 25 BTC gauti už naujo bloko sukūrimą, o taip pat ir 0.0909 BTC už transakcijų mokesčius.

```python

# `rpc_block.py` example
from bitcoin.rpc import RawProxy

p = RawProxy()

# The block height where Alice's transaction was recorded
blockheight = 277316

# Get the block hash of block with height 277316
blockhash = p.getblockhash(blockheight)

# Retrieve the block by its hash
block = p.getblock(blockhash)

# Element tx contains the list of all transaction IDs in the block
transactions = block['tx']

block_value = 0

# Iterate through each transaction ID in the block
for txid in transactions:
    tx_value = 0
    # Retrieve the raw transaction by ID
    raw_tx = p.getrawtransaction(txid)
    # Decode the transaction
    decoded_tx = p.decoderawtransaction(raw_tx)
    # Iterate through each output in the transaction
    for output in decoded_tx['vout']:
        # Add up the value of each output
        tx_value = tx_value + output['value']

    # Add the value of this transaction to the total
    block_value = block_value + tx_value

print("Total value in block: ", block_value)
```

## Užduoties formuluotė (Preliminarus terminas: 2019-11-29)

1. Panaudojant `python-bitcoinlib` biblioteką, Python aplinkoje realizuokite programą, apskaičiuojančią  transakcijos (pvz.`0627052b6f28912f2703066a912ea577f2ce4da4caa5a5fbd8a57286c345c2f2`) mokestį?

   - Patobulinkite programą, kad ji gebėtų apskaičiuotų bet kurios įvestos Bitcoin transakcijos mokestį.
   - Apskaičiuokite, kiek kainavo atlikti (2019-09-06) vieną vertingiausių transakcijų Bitcoin tinkle, kurios hash'as yra: `4410c8d14ff9f87ceeed1d65cb58e7c7b2422b2d7529afc675208ce2ce09ed7d`

2. Panaudojant `python-bitcoinlib` biblioteką, Python aplinkoje realizuokite programą, kuri iš  atitinkamos bloko header'io informacijos "patikrintų", kad bloko hash'as yra teisingas. Kaip pagalbine primone, rekomenduojame naudotis šiuo **wiki** šaltiniu: [Block hashing algorithm](https://en.bitcoin.it/wiki/Block_hashing_algorithm)

