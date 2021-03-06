Developing document for Mac and Linux
-------------------------------------

The Peatio installation consists of setting up the following components:

1. Requirements
2. Bitcoind
3. Peatio


## 1. Requirements

* XCode and/or the XCode Command Line Tools.
* Homebrew
* Ruby 2.1.0, using [RVM](http://rvm.io/) or [rbenv](https://github.com/sstephenson/rbenv)
* MySQL
* Redis
* PhatomJS
* qrencode
* Pusher

** More details are in the [requirements doc](doc/install/requirements.md)

### Pusher

Peatio dependence [Pusher](http://pusher.com) service, you can change your key in `config/application.yml` file for production environment. we support development key and secret in repo, is only support test and development environment.

     PUSHER_APP: 65910
     PUSHER_KEY: 50d404c35db92d736a57
     PUSHER_SECRET: 75d6e6685209cc60cc4d
     
More details to visit [pusher official website](http://pusher.com)

##### Install PhatomJS

**For Mac**

    brew install phantomjs

**For Linux**

    sudo apt-get install -y libfontconfig libfontconfig-dev libfreetype6-dev

* Download the [32 bit](https://phantomjs.googlecode.com/files/phantomjs-1.9.2-linux-i686.tar.bz2)
or [64 bit](https://phantomjs.googlecode.com/files/phantomjs-1.9.2-linux-x86_64.tar.bz2)
binary.
* Extract the tarball and copy `bin/phantomjs` into your `PATH`

** More details are in the [poltergeist](https://github.com/jonleighton/poltergeist/blob/master/README.md) doc.

##### Install qrencode

**For Mac**

    brew install qrencode

**For Linux**

    sudo apt-get install qrencode libqrencode-dev

## 2. Bitcoind

#### Install bitcoind

**For Mac**

Download and Install [Bitcoin](http://bitcoin.org/en/download)    

**For Linux**

    sudo add-apt-repository ppa:bitcoin/bitcoin
    sudo apt-get update
    sudo apt-get install -y bitcoind

#### Configure bitcoind

Insert the following lines into your bitcoin.conf, and replce with your username and password.

    server=1
    daemon=1
    rpcuser=INVENT_A_UNIQUE_USERNAME
    rpcpassword=INVENT_A_UNIQUE_PASSWORD

    # If run on the test network instead of the real bitcoin network
    testnet=1


**For Mac**

    ~/Library/Application\ Support/Bitcoin/bitcoin.conf

**For Linxu**

    ~/.bitcoin/bitcoin.conf


#### Start Bitcoind

**For Mac**

    open /Applications/Bitcoin-Qt.app --args -server

**For Linux**

    bitcoind


## 3. Peatio

##### Clone the project

    git clone git@github.com:peatio/peatio.git
    cd peatio
    bundle install

##### Config database settings:

    vim config/database.yml

    # Initialize the database and load the seed data
    bundle exec rake db:setup

##### Config email smtp settins:

    TODO

##### Run Peatio

    rake environment resque:work QUEUE=*
    rails server

##### Visit [http://localhost:3000](http://localhost:3000)

    user: admin@peatio.dev
    pass: Pass@word8


