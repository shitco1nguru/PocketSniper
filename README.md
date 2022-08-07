# PocketSniper
Pocket Sniper tutorial, readme, etc.
Hello! Welcome to PocketSniper readme. I hope it will help you not to miss the moonshots we all desire!
In this short guide I will explain how to use it safely.
First of all, what does this bot do? It interacts directly with uniswap contract, bypassing the UI and Metamask (aka router buy/sell with unlimited slippage). It is also possible to send several transactions in 1 block. Some contracts prohibit this, so only first one will come through. 
There are TWO types of buying. 
For the first one (/buytokens command, description further) you specify the EXACT amount of ETH you want to spend. Default is 0.001 ETH. On this tx you will spend exactly 0.001 ETH and receive the amount of tokens based on the current price.
Second option (/limitbuy command, description further) - you specify the amount of TOKENS you want to get. So if you know that max buy is 5000000 tokens, you just specify it with the /maxbuy command (description furher). After sending the tx, the bot will buy 5000000 spending 0.001 ETH AT MOST. It means that if the price moves more, the tx will fail. So you can use the /amount command to set the maximum ETH you are ready to spend on this buy. 
DO NOT USE THE BOT TO BUY 0% TAX TOKENS! You will be frontrun and REKT! Maybe only small amounts (no more than 0.1 ETH) can be ok. But no guarantees.

In the archive you will find the following:
 
Don't change or move the abi folder, it's needed for the bot to count the bag size in ETH. 
buyBot.exe is the bot itself.
startNode.bat - batch file that will launch the light node on your PC (full description further).
parameters.txt is the config file
It has the following:
 

ONLY change stuff inside the quotation marks, otherwise the program will throw an error. 
DO NOT CHANGE "to", "privateKey", "httpnode" or ''wsnode'' words please, otherwise it won't work!
As you can see, you have preinstalled infura links. So you can use bot right "out of the box", not bothering with setting up your own node. But that's not the fastest way for sure. You can change the node links to any other you want. If you change it to "local" then local node will be used.
Private key is not the seed phrase  but a private key, unique for each wallet. Without it, bot won't be able to sign and send any transaction. You should export it from metamask yourself.
Here is how it can be done: https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key

Please be sure when you paste the private key to the parameters.txt add 0x in the beginning! From metamask it will be copied without it!
IMPORTANT!
"to" - the wallet that will receive the tokens.
"privateKey" - relates to the wallet that will BUY the tokens. 
Ideally - you create a COMPLETELY NEW wallet and paste private key from it to the bot, add send there only small sums of money that you will use for buying tokens and that's it. DO NOT KEEP a lot on the BUYING WALLET! It's safe, but additional level of security is never a bad idea.
As a result, ready to use parameters.txt will look like this:
 
In order for the bot to work EXE should be ALWAYS on. You can turn it on when you're trading, or out of home and turn off when you don't need it. 
If you update data in parameters.txt you need to RELAUNCH the exe file!
If you want to get it running 24/7 I recommend buying the cheapest VPS (virtual private server) and launch it there.
Only one instance of bot running is allowed. If you see the following error:

error: [polling_error] {"code":"ETELEGRAM","message":"ETELEGRAM: 409 Conflict: terminated by other getUpdates request; make sure that only one bot instance is running"}
REVOKE THE LINK VIA BOTFATHER withdraw ETH from buying account and DM ME ASAP! 
Laucnhed buyBot.exe looks like this
 
Shows the date when trial will end, the trading address and the status of private key and the nodes

AVAILABLE COMMANDS 
Pay attention that every input to the bot (changing token, buying amount, etc) should be typed in REPLY to the bot's message! It pops automatically!
/checkbuy
Checks the buying parameters, looks like following
 
/checksell
Same for sell parameters
 
/token
Sets the buyable/sellable token
 
After setting the token, /checkbuy and /checksell will look like on the following screenshot
 
Shows the token address, link to token's etherscan page
Your current balance of chosen tokens. 
For /checkbuy it shows amount of ETH you are going to spend on buying the tokens and the amount to tokens for /limitbuy
for /checksell shows the percentage of your tokens you are going to sell and approximate bag worth in ETH
/amount 
Sets the amount of ETH for spending on buying
Also count as a limit for /limitbuy command (description further)
 
/setfee
Set current priority gas fee. The more it's set - the faster the tx will mine. Don't put lower than 2. Better 4-5 or even more.
 
/gas 
Shows the current network gas
 
/approve - approves the tokens for trading on uniswap V2

/setsellmodifier
Setting the amount of tokens you want to sell in % of your total CURRENT bag
Must be between 0 and 1. For example 0.5 - 50% Use .  (dot) and not , (comma) as dividor!!!!
 
/safemode  Toggles the trading. ON and OFF. Default is OFF. Just in case you want to protect yourself from a missclick.
 
 
/selltokens - works as intended when trading is ON.
/buytokens 
Spends EXACT amount of ETH mentioned in /amount command. When trading is ON, /checkbuy command also shows 2 clickable buttons for buying right after that! 
 
Clicking the button will trigger the specified buy operation. 
/maxbuy - sets the EXACT amount of tokens to buy (for limit buy ONLY) WITHOUT DECIMALS! DECIMALS ADDED AUTOMATICALLY!
 
So with current parameters after clicking the button or sending the /limitbuy command the bot will buy 4422 tokens of MetaReset, spending MAXIMUM 0.01 ETH. If the current price will be above 0.01 ETH the tx will fail. So you can manage your risk in this way
Below I made 2 transactions, buying 3300 tokens of MetaReset each. First one I made clicking the 1 button, second tx went on clicking the 2 button. On this very screenshot order is wrong (txHash goes before the "asking", I've fixed it in the release version). As you can see, both TXes were mined in same block.
here are they:
https://etherscan.io/tx/0xe6027d4f8c42c93e54128ba29207fe5bcaa005a1c842cc73b327a338374c1c92
https://etherscan.io/tx/0x1bb21d4eefc0bf71eaa7f3e2a9b50a3d3e50f19815ca0b63e410ee28a0daa75b
 
Result of ordinary (without button) and approve looks like that:
 
/mybalance - shows your current account balance in ETH
 

There are 4 rows with red or green circles on the /checksell or /checkbuy responses.
/buytokens and /selltokens will work ONLY if all 4 are green.

LIGHT NODE LAUNCHING!
To set your own node go here and download the latest GETH client.
https://geth.ethereum.org/downloads/

After installing just launch the"startNode.bat". You will see the node syncing. Light node is syncing relatively fast but it will take some time (10 mins approx). You can have it running 24/7 if you want of course. 
The following setup should be in place in parameters.txt for local node usage.
 
Synced node will look like this, pay attention to count = 1 and that there's no "age" flag on the right.
 

If you want to use cloud node choose any provider
https://www.quicknode.com/
https://chainstack.com/
https://infura.io/
There are many others, you can google some more.
Infura and chainstack are free so I guess they would be a better choice.
Chainstack will likely be faster. But of course the fastest - local node.


