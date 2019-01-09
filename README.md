# BurstcoinTestNetHow-To
NewTestNet How to

To connect to the new test net, you will need to install the latest released version of the wallet. You can find instructions on setting up the wallet from the Burstcoin website (https://burst-coin.org). Keep in mind there may be scenarios where you would like to have your own private test net, say in case of some future revisions that might rewuire a fork for adding to the current chain. In this case you could simply change the value for DEV.P2P.BootstrapPeers, the new value would be your localhost. Keep in mind if you are missing any parts of this configuration you will most likely encounter issues that are resolved by the values below. Again this is for testing purposes and DO NOT USE YOUR REAL PASSPHRASE. 

If you wish to be added as a peer to the testnet simply fork and create a Pull Request with your ip address added. All volunteers welcome. We do require you to check in weekly in discord so that you are aware of updates currently being deployed to test net and actively want to participate. If at any time you would like your ip removed, simply make a pull request and remove it. 

For those that would also like to mine while running a node to help with a developer faucet on the test net. Then please create a new id, sync your peer, and start solo mining to your localhost(port 6876). Currently there is no mining pool on the test net if someone is interested in starting a small pool on the testnet, it would be greatly appreciated. If you want to add information to this page, please submit a pull request with desired changes. 


Edit the following in conf/brs-default.properties: 



DEV.Offline = no

#Use testnet, leave set to false unless you are really testing.
#Never unlock your real accounts on testnet! Use separate accounts for testing only.
#When using testnet, all custom port settings will be ignored,
#and hardcoded ports of 6874 (peer networking), 6875 (UI) and 6876 (API) will be used.
DEV.TestNet = yes

#Database connection JDBC url to use with the test network, if DEV.TestNet

DEV.DB.Url = jdbc:mariadb://localhost:3306/burstwalletdev

DEV.DB.Username = burstwallet

DEV.DB.Password = easypassword

#Time Acceleration in Offline/TestNet configurations (1 = normal time, 2 = twice as fast ...)

DEV.TimeWarp = 1

#Peers used for testnet only.

DEV.P2P.BootstrapPeers = 3.16.150.48

#Testnet only. These peers will always be sent rebroadcast transactions. They are also automatically added to 

DEV.P2P.BootstrapPeers, so no need for duplicates.

DEV.P2P.rebroadcastTo = 3.16.150.48

#Force winning with every deadline

DEV.mockMining = ooff

#Enter a version. Upon exit, print a list of peers having this version.

DEV.dumpPeersVersion =

#Force re-validation of blocks and transaction at start.

DEV.forceValidate = off

#Force re-build of derived objects tables at start.

DEV.forceScan = off

DEV.P2P.NumBootstrapConnections = 1

BRS.allowedBotHosts = *

DEV.digitalGoodsStore.startBlock = 0

DEV.automatedTransactions.startBlock = 0

DEV.atFixBlock2.startBlock = 0

DEV.atFixBlock3.startBlock = 0

DEV.atFixBlock4.startBlock = 0

DEV.preDymaxion.startBlock = 0

DEV.poc2.startBlock = 0

If you just need testnet wallet for testing please use this link (http://3.16.150.48:6876/index.html#). If you want to use your own desired peer, you can just change ip addresses. 
