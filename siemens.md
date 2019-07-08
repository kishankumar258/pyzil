#  Zilliqa Documentation


Name: Kishan Kumar

Emp No.: 75071592

Email (Siemens): kishan.kumar@siemens.com

Email (Gmail): kishankumar.sky@gmail.com

Contact No.: 9793377240

## To study Blockchain and Bitcoin and Ethereum concepts

Coursera link: https://www.youtube.com/channel/UCNcSSleedtfyDuhBvOQzFzQ/feed

Learning ethereum use that decentralised network provides quite a many advantage over the centralised authority.


## Zilliqa(www.zilliqa.com)
Zilliqa is a scalable, secure public blockchain platform. It's the first public blockchain platform that implemented sharding and achieved a throughput of 2828 transactions per second in its testnet.
This enables new use cases that have high-throughput demands that were not previously possible on legacy public blockchain platform.

More detailed description about Zilliqa: https://blog.zilliqa.com/zilliqa-hello-world-50b76983cd12


## Network Sharding in Zilliqa


Network Sharding is a mechanism that allows the Zilliqa network to be divided into smaller groups of nodes each referred to as a shard. Simply put, imagine a network of 1,000 nodes, then, one may divide the network into 10 shards each composed of 100 nodes. For security reasons, a shard must be sufficiently large, say with more than 600 nodes.

More on sharding its challenges and how zilliqa solves it:https://blog.zilliqa.com/https-blog-zilliqa-com-the-zilliqa-design-story-piece-by-piece-part1-d9cb32ea1e65

## Zilliqa Consensus
The blockchain network uses a hybrid combination of Proof of Work (PoW) protocol and Byzantine Fault Tolerant (pBFT) protocol. The PoW protocol is used to establish the mining identity on the network, to perform sharding on the network and also protect the users against the Sybil attacks.

During a Sybil attack, malicious nodes create multiple identities and try to influence the decision-making process.

The current transaction king VISA can process 8,000 transactions per second, Ziliqa, on the other hand, is currently at 2,000 transactions on its trial run in May 2018

Zilliqa employs practical byzantine fault tolerance protocol aka PBFT for consensus within each shard. The protocol was proposed by Castro and Liskov in 1999. It runs under the assumption that before the start of the protocol a fraction say up to 1/3 of the nodes in each shard can be malicious.
In PBFT, all the nodes within a consensus group (a shard in our case) are ordered in a sequence, and it has one primary node (aka a leader) and the others are referred to as backup nodes. Every round of PBFT has three phases as discussed below:

   * Pre-prepare phase: .
   * Prepare phase:
   * Commit phase:
   
PBFT is clearly a promising solution to reach consensus in Zilliqa. However, it has a major drawback: it is efficient only when the size of the consensus group is small, i.e., less than 50. But, as discussed in our previous article, for security reasons, the shard size in Zilliqa has to be at least 600. We reduce it using a primitive called multi-signature.

Consensus protocol blog details:https://blog.zilliqa.com/the-zilliqa-design-story-piece-by-piece-part-2-consensus-protocol-e38f6bf566e3
## Multi-Signatures

Multi-signatures are a cryptographic primitive to aggregate n signatures on a message from n parties into a signature of constant size.

The very detailed blog for multisignatures.

A multi-signature scheme basically runs in two steps. In the first step of the protocol, each node will send its public key to the aggregator. All the public keys are then aggregated to generate a single public key. Depending on the mathematical form of the keys, the aggregation could simply be a simple addition or a multiplication.

E.g., Aggregated Public key = Public key_1 + Public key_2 + …. + Public key_n.
The aggregated public key can then be forwarded to the verifier who can use it to verify an aggregated signature. The aggregator also sends the message to be signed to each of the signers.

In the second step, the aggregator initiates an interactive protocol with each of the signers. The interactive protocol runs in three phases:

Commit phase: In the commit phase, each node generates some randomness and commits to it. For those who do not understand what a cryptographic commitment is, consider the following analogy: each node will secretly roll a dice, write down the outcome on a sheet of paper and put it in a box, lock it and send it to the aggregator. The aggregator should not be able to open the box.

Challenge phase: In the challenge phase, the aggregator first aggregates each commitment again using addition or multiplication. It then generates a challenge using the aggregated commitment, the aggregated public key and the message. The challenge is then sent to each node. The challenge is later used to confirm that each node indeed knows the private key for the public key. This is similar to how regular digital signatures work, where a signature proves that the signer indeed knows the private key.

Response phase: Each node then responds to the challenge by sending a response that requires the use of its private key. Responses are then aggregated by the aggregator. Each response is sort of a proof that the signer knows the private key for its public key.
The final aggregated signature is then the pair (challenge, aggregated response) which can be verified against the aggregated public key generated in the first step.

Note that the size of the aggregated signature is constant and does not depend on the number of signers.
When the verifier checks the aggregated signature, it does not check whether each signer has properly followed the protocol, it only checks whether all the signers have collectively followed the protocol and have proven the knowledge of their private keys. Hence, the verifier makes an all-or-nothing decision.

https://blog.zilliqa.com/the-zilliqa-design-story-piece-by-piece-part-3-making-consensus-efficient-7a9c569a8f0e
.

## The launch of Zilliqa testnet and mainent

https://blog.zilliqa.com/zilliqa-mainnet-the-launch-and-beyond-4cd7e113369f

https://blog.zilliqa.com/zilliqa-testnet-v2-0-codename-d24-ea7ca75adc70

The website for seeing zilliqa transactions history and logs for testnet and mainnet

https://viewblock.io/zilliqa

# Technical part


For accessing the mainnet or testnet of zilliqa blockchain, we need to use an api client.
Zilliqa provides its clients in javascript, java, ruby, python and cURL could be used.
I have used python client "pyzil" for whole of the implementation and testing.

Pyzil github repo: https://github.com/deepgully/pyzil

Note:pyzil supports python 3 only first install python3 then can run python scripts .
## Installation of pyzil client

1-Install python 3

2-Make python 3 as default by
    You can try the command line tool update-alternatives.
    
    $ sudo update-alternatives --config python
    
   If you get the error "no alternatives for python" then set up an alternative yourself with the following command:
    
    $ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10

3-Installing pip for Python 3

Ubuntu 18.04 ships with Python 3, as the default Python installation. Complete the following steps to install pip (pip3) for Python 3:

Start by updating the package list using the following command:

	   $ sudo apt update
Use the following command to install pip for Python 3:

	   $ sudo apt install python3-pip
    
The command above will also install all the dependencies required for building Python modules.
Once the installation is complete, verify the installation by checking the pip version:

	$ pip3 --version

The version number may vary, but it will look something like this:
pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)

4-  `enter code here`
or from source
git clone https://github.com/deepgully/pyzil
cd pyzil
pip install -r requirements.txt
python setup.py install

## Note on api docs
The whole api docs for zilliqa can be found at: https://apidocs.zilliqa.com/?python#getnetworkid

For mainnet or testnet all the methods here works except that of creating transaction for that we need to prepend active_chain with chain.

And it should work

So, `params = active_chain.build_transaction_params(my_key, **payload)` should be `params = chain.active_chain.build_transaction_params(my_key, **payload)` 

and `active_chain.api.CreateTransaction(params)`  should be `chain.active_chain.api.CreateTransaction(params)`

also nonce is need to be written inside the params block and the address must be prepended with "0x". Now this works but for some reason this does not reflect on the zilliqa view block website.

## Sending ZIL's

So we need to make transactions from the method given on pyzil github repository by first importing these library of python
      
### Import pyzil
```python
from pprint import pprint

from pyzil.crypto import zilkey
from pyzil.zilliqa import chain
from pyzil.zilliqa.units import Zil, Qa
from pyzil.account import Account, BatchTransfer
```

 
#### Set Active Chain, MainNet or TestNet
```python
chain.set_active_chain(chain.MainNet)  
```  

#### ZILs Transaction
```python
# load account from wallet address
account = Account(address="95B27EC211F86748DD985E1424B4058E94AA5814")
balance = account.get_balance()
print("{}: {}".format(account, balance))

# load account from private key
# private key is required to send ZILs
account = Account(private_key="05C3CF3387F31202CD0798B7AA882327A1BD365331F90954A58C18F61BD08FFC")
balance2 = account.get_balance()
print("Account balance: {}".format(balance2))

# to_addr must be bech32 address or 20 bytes checksum address
to_addr = "zil1k5xzgp8xn87eshm3ktplqvs9nufav4pmcm52xx"
# send ZILs
txn_info = account.transfer(to_addr=to_addr, zils=2.718)
pprint(txn_info)
txn_id = txn_info["TranID"]

# wait chain confirm, may takes 2-3 minutes on MainNet
txn_details = account.wait_txn_confirm(txn_id, timeout=300)
pprint(txn_details)
if txn_details and txn_details["receipt"]["success"]:
    print("Txn success: {}".format(txn_id))
else:
    print("Txn failed: {}".format(txn_id))
```  


## Now, we can see that the chain library needs to be set and it supports mainnet and testnet only.

## Contract Deployment on MainNet or TestNet.
Contracts can be deployed on testnet or mainnet as on the github repo from pprint import pprint

## Zilliqa Smart Contract
```python
from pprint import pprint
from pyzil.zilliqa import chain
from pyzil.account import Account
from pyzil.contract import Contract


chain.set_active_chain(chain.TestNet)

account = Account.from_keystore("zxcvbnm,", "zilliqa_keystore.json")
```

### Get contract from address
```python
address = "45dca9586598c8af78b191eaa28daf2b0a0b4f43"
contract = Contract.load_from_address(address, load_state=True)
print(contract)
print(contract.status)
pprint(contract.state)
contract.get_state(get_code=True, get_init=True)
pprint(contract.code)
pprint(contract.init)
pprint(contract.state)
```

### New contract from code
```python
code = open("HelloWorld.scilla").read()
contract = Contract.new_from_code(code)
print(contract)

# set account before deploy
contract.account = account

contract.deploy(timeout=300, sleep=10)
assert contract.status == Contract.Status.Deployed
```

### Get contracts
```python
owner_addr = account.address
contracts = Contract.get_contracts(owner_addr)
pprint(contracts)
contracts2 = account.get_contracts()
pprint(contracts2)

assert contracts == contracts2
```

### Call contract
```python
contract_addr = "45dca9586598c8af78b191eaa28daf2b0a0b4f43"
contract = Contract.load_from_address(contract_addr)

contract.account = account

resp = contract.call(method="getHello", params=[])
pprint(resp)
pprint(contract.last_receipt)

resp = contract.call(method="setHello", params=[Contract.value_dict("msg", "String", "hi contract.")])
pprint(resp)
pprint(contract.last_receipt)

resp = contract.call(method="getHello", params=[])
pprint(resp)
pprint(contract.last_receipt) 

```

## For setting up local network for testing zilliqa

           Minimum system requirements
To run Zilliqa, we recommend the following as the minimum system requirements:

x64 Linux operating system such as Ubuntu
Intel i5 processor or later
2 GB RAM or higher
Build Dependencies
Ubuntu 18.04


##  Build from Source Code

Build Zilliqa from the source:

download the lastest stable Zilliqa source code

$ git clone git@github.com:Zilliqa/Zilliqa.git
$ cd Zilliqa && git checkout tag/v4.6.1

                build Zilliqa binary
$ ./build.sh


# Boot up a local testnet for development
Run the local testnet script in build directory:

$ cd build

&& ./tests/Node/pre_run.sh

This setups 20 local nodes and prestarts 10 of them after cleaning previous nodes also it setup the lookup node.

&& ./tests/Node/test_node_lookup.sh

This starts the lookup node.

&& ./tests/Node/test_node_simple.sh

This starts the local nodes and starts the blockchain by making the genesis account with a balance and then sending the balance to all the nodes adding up transaction blocks and sending commands.

We can view this in the zilliqa logs txt file in the node001 folder of lookup run.

Note: When running the scripts in the /tests/Node in the build directory change the python to python2 since all the python scripts at /tests/zilliqa are written in python 2 but we have made python 3 as the default.

So running the scripts gives error on print statements and also for the ASCII code of changing hexadecimal to string while adding.

Logs of each node can be found at ./local_run.

To terminate Zilliqa:

$ pkill zilliqa

NOTE : The master branch is not for production as development is currently being worked constantly, please use the tag releases if you wish to work on the version of Zilliqa client that is running live on the Zilliqa blockchain. (Current live version tag release is v4.6.1)


## Development and Code along with errors and their solutions

Github repo of zilliqa provides the scripts for running a network of zilliqa nodes locally and we can interact with the blockchain using the same api as that of mainnet or testnet bu the problem is chain supports only mainnet or testnet so the method was by setting the endpoint as

new_api=ZilliqaAPI(endpoint="http://localhost:4201")

this will work for all the api scripts but for creating tracsaction this will not work as setting chain is mandatory.

Now by talking on gitter forum and their help they told to make changes to a file on pyzil github repo chain.py which is the file by

One way is to add localhost yourself after MainNet here:

https://github.com/deepgully/pyzil/blob/c712f5f0dac382ca2ee038343ef2a4cccc154437/pyzil/zilliqa/chain.py#L113

LocalNet = BlockChain("http://localhost:4201", version= 131073, network_id= 2)

Then:

chain.set_active_chain(chain.LocalNet)

but this will produce this error

After doing this I get this error chain.set_active_chain(chain.LocalNet) AttributeError: module 'pyzil.zilliqa.chain' has no attribute 'LocalNet'

I had forked the pyzil repo made changes and then setup pyzil.

The problem could of integration to python pyzil library I tried various changes by making changes to source of python library and other places but that also does not work.

Then one way I though was to change in chain.py file and also run that file only as the main api script

The steps are:

In the main function make the object for the blockchain class using the above arguments for url,version and network _id then we can write the set_active_chain and get_active_chain methods in blockchain class then set active chain to LocalNet by using chain.set_active_chain(LocalNet) inside main function.

Then we can use the same way sending transactions as give above for testnet or mainnet as in the github repo.

Now important note is getting the addresses and the public private key of nodes.

When we ran the scripts for blockchain creation, we got the local_run folder in build directory this contains keys.txt file which contains the public and private keys for the nodes created and one lookup_run foder is created which contains the public private key for the lookup node.




## More Development 

Define lookup node here.

Now in the node folder we can find that in zilliqa logs the address of lookup node. Similarly, In the node folder inside local run opening the zilliqa logs you get the information on the address of the node.This is the checksum address when we add'0x"I the start and can be used to getbalance and other scripts. But when sending transactions to testnet or mainnet this checksum address will work but when sending on LocalNet this gives and error. Therefore, chatting on zilliqa forum I get his thing



Therefore, I converted the checksum address of nodes to bech32 address using

to_addr=bech32.encode("zil", utils.hex_str_to_bytes(to_addr))

after importing necessary pyzil library codes.

The zil.py file is uploaded to the forked repository of pyzil at

https://github.com/kishankumar258/pyzil/blob/master/pyzil/zilliqa/zil.py.

This could be run in python 3 after starting the blockchain and

Smart Contract Trasnsaction on the local network

Smart Contracts are not enabled by default and knew on this as of gitter channel as below



To install the scilla binary fitsr install the scilla dependencies. As in the github repo

Make sure opam version is 4.06 and also needs to download the opam package ctypes as that was not accessible

For larger contracts deployment




For reading use only

Documentation: https://apidocs.zilliqa.com/?python#introduction

Python api: https://github.com/deepgully/pyzil

Java Api: https://github.com/Zilliqa/Zilliqa-JavaScript-Library

https://docs.zilliqa.com/techfaq.pdf Zilliqa FAQ

the python files are written in python 2 while zilliqa runs mainly on python 3 the pyzil one

one small but important error was concatenating byte and strings in python 3 and python2.

Python 2 allows automatic change while python3 lacks it. have a lok

https://github.com/Zilliqa/Zilliqa/pull/120

some details for docker image container

A very good video to understand docker networking using bridge connections and how to create and ping containers

https://www.youtube.com/watch?v=Tx12haz-4VA

A good link for quick ziliqa overview

https://info.binance.com/en/research/ZIL-2019-05-15.html#section1

References:

Github repo of zilliqa: https://github.com/Zilliqa/Zilliqa

Github repo of pyzil: https://github.com/deepgully/pyzil

JSON api documentation: https://apidocs.zilliqa.com/#introduction

Help provided on the topics mostly on gitter channel of zilliqa https://gitter.im/Zilliqa/General?source=orgpage by evesnow91 https://github.com/evesnow91

And AmritKumar

Sending 100ZIL
