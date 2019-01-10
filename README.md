# BurstcoinTestNetHow-To
NewTestNet How to

To connect to the new test net, you will need to install the latest released version of the wallet. You can find instructions on setting up the wallet from the Burstcoin website (https://burst-coin.org). Keep in mind there may be scenarios where you would like to have your own private test net, say in case of some future revisions that might rewuire a fork for adding to the current chain. In this case you could simply change the value for DEV.P2P.BootstrapPeers, the new value would be your localhost. Keep in mind if you are missing any parts of this configuration you will most likely encounter issues that are resolved by the values below. Again this is for testing purposes and DO NOT USE YOUR REAL PASSPHRASE. 

If you wish to be added as a peer to the testnet simply fork and create a Pull Request with your ip address or hostname to get added. All volunteers welcome. We do require you to check in weekly in discord (https://discord.gg/9S3eUBy) (testnet channel) so that you are aware of updates currently being deployed to test net and actively want to participate. If at any time you would like your ip removed, simply make a pull request and remove it. 

For those that would also like to mine while running a node to help with a developer faucet on the test net. Then please create a new id, sync your peer, and start solo mining to your localhost(port 6876). Currently there is no mining pool on the test net if someone is interested in starting a small pool on the testnet, it would be greatly appreciated. If you want to add information to this page, please submit a pull request with desired changes. 


Edit/add the following in conf/brs.properties: 
````
#### DATABASE ####
# For MariaDB
#DEV.DB.Url=jdbc:mariadb://localhost:3306/DatabaseName
DEV.DB.Username=DatabaseUser
DEV.DB.Password=somepassword
DEV.DB.Connections=10

#### TestNet Settings ####
# Use testnet, leave set to false unless you are really testing.
# Never unlock your real accounts on testnet! Use separate accounts for testing only.
# When using testnet, all custom port settings will be ignored,
# and hardcoded ports of 6874 (peer networking), 6875 (UI) and 6876 (API) will be used.
DEV.Offline = no
DEV.TestNet = yes
# Time Acceleration in Offline/TestNet configurations (1 = normal time, 2 = twice as fast ...)
DEV.TimeWarp = 1
# Force winning with every deadline
DEV.mockMining = off
DEV.preDymaxion.startBlock = 0
DEV.poc2.startBlock = 0
DEV.digitalGoodsStore.startBlock = 0
DEV.automatedTransactions.startBlock = 0
DEV.atFixBlock2.startBlock = 0
DEV.atFixBlock3.startBlock = 0
DEV.atFixBlock4.startBlock = 0
DEV.P2P.NumBootstrapConnections = 1
BRS.allowedBotHosts = *
# Only use this Hosts if you really want to use the testnet!!!
DEV.P2P.BootstrapPeers = 3.16.150.48; aya.onthewifi.com; testnet.burst.fun; testddns.gotdns.com; test-burst.megash.it
DEV.P2P.rebroadcastTo = 3.16.150.48; aya.onthewifi.com; testnet.burst.fun; testddns.gotdns.com; test-burst.megash.it
# Allow the wallet to discover new peers, store them in the DB and reuse them after restart.
P2P.savePeers=true
P2P.usePeersDb=true
P2P.getMorePeers=true

#### Personal Customization #### 
P2P.shareMyAddress=true
# our examples are aya.onthewifi.com OR testnet.burst.fun OR testddns.gotdns.com OR test-burst.megash.it
P2P.myAddress=fqdn.to.your.wallet
# Change to your needs, this will be displayed in Peer Overview, modify this to whatever you want.
P2P.myPlatform=Official burst.megash.it TestNET Node
# Enable/Disable API requests used for blockchain and database manipulation.
#API.Debug=false


#### Additional Stuff ####
# Enter a version. Upon exit, print a list of peers having this version.
DEV.dumpPeersVersion =
# Force re-validation of blocks and transaction at start.
DEV.forceValidate = off
# Force re-build of derived objects tables at start.
DEV.forceScan = off


````

If you just need testnet wallet for testing please use this link (http://3.16.150.48:6876/index.html#). If you want to use your own desired peer, you can just change ip addresses. 


To make your peer public you will need to change the following in your properties file.
````
#API network 
API.Port = 8125 
API.Listen = 0.0.0.0
API.allowed = *;0.0.0.0
````
If for any reason you need to reset your peer, a fast easy way to do it is as follows:

Stop node, in a terminal execute:
````
mysql -u root
````
Once in the mysql shell execute the following commands, assumption is made $yourdb name is your database's name and $youruser is well your user.
````
DROP DATABASE $yourdatabase;
CREATE DATABASE $yourdatabase;
ALTER DATABASE $yourdatabase CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
````
Start node again, wait till sync is complete. 

If you hit any snags, let me know. Also feel free to update this via PR. Thanks.

Originally adapted from the following: https://burstwiki.org/wiki/Testnet

Thank you PoCC and BurstWiki contributors!
