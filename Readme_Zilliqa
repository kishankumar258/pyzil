# Zilliqa Client in python

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

## Install

```shell
pip install pyzil
```
or from source
```shell
git clone https://github.com/deepgully/pyzil
cd pyzil
pip install -r requirements.txt
python setup.py install
```
## For TestNet 
testcheck.py could be used for sending from one account to another. 
1.Private key for the account from which ZILs is to send is needed.
2-Public address to which the ZILs are to send is needed.

Send_testnet.py could be used for having a cycle of transaction.
1-4 accounts needs to be created to use this.

# For Local Setup

## Build Dependencies

* Ubuntu 16.04:

    ```bash
    sudo apt-get update
    sudo apt-get install git libboost-system-dev libboost-filesystem-dev libboost-test-dev \
        libssl-dev libleveldb-dev libjsoncpp-dev libsnappy-dev cmake libmicrohttpd-dev \
        libjsonrpccpp-dev build-essential pkg-config libevent-dev libminiupnpc-dev \
        libprotobuf-dev protobuf-compiler libcurl4-openssl-dev libboost-program-options-dev gawk
    ```

## Build from Source Code

Build Zilliqa from the source:

```shell
# download the lastest stable Zilliqa source code
$ git clone git@github.com:Zilliqa/Zilliqa.git
$ cd Zilliqa && git checkout tag/v4.6.1

# build Zilliqa binary
$ ./build.sh
```

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


