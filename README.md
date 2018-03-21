<h1 style="color: green;">Create a private Ethereum Network in local</h1>
<div>
	<ol>
		<li><h2>Install and Update Homebrew</h2>
			<ul>
				<li>Install Homebrew: <b>ruby -e “$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"</b></li>
				<li><b>brew update</b></li>
				<li><b>brew upgrade</b></li>
			</ul>
		</li>
		<li><h2>Install Ethereum</h2>
			<ul>
				<li><b>brew tap ethereum/ethereum</b></li>
				<li><b>brew install ethereum</b></li>
			</ul>
		</li>
		<li><h2>Node creation</h2>
			<ul>
				<li>create a private folder e.g.: <b>mkdir privateEth</b></li>
				<li>Go inside the directory: <b>cd privateEth</b></li>
				<li>Create a genesis file: <b>touch genesis.json</b></li>
				<li>Copy the contents of genesis file from the github repository <a href="https://github.com/subhasmitasahoo/Ethereum-Private-Network" download>genesis file</a></li>
				<li>Instantiate the genesis block: <b>geth --datadir ./ethdata1 init ./genesis.json</b></li>
				<li>Start the node: <b>geth --datadir="./ethdata1" --networkid 55580 --nodiscover --rpcport "8546" --rpccorsdomain "*" --port 30304</b></li>
				<li>Copy the IPC end point displayed at the end (Ex. /Users/user1/Desktop/MonthlyEngiTalk/privateEth/private/geth.ipc)</li>
			</ul>
		</li>
		<li><h2>Geth Console</h2>
			<ul>
				<li>Open a new console tab</li>
				<li>Start the geth console: <b>geth attach (Paste the end point)</b></li>
				<li>To see the list of current accounts: <b>eth.accounts</b></li>
				<li>To create an account <b>personal.newAccount()</b></li>
				<li>Balance of any account(Here index is 0): <b>eth.getBalance(eth.accounts[0])</b></li>
				<li>To get the balance in ether: <b>web3.fromWei(eth.getBalance(eth.coinbase),"ether")</b></li>
				<li>To see the etherbase account: <b>eth.coinbase</b></li>
				<li>Balance of etherbase account: <b>eth.getBalance(eth.coinbase)</b></li>
				<li>To start the miner (This adds balance in etherbase account)<b>miner.start()</b></li>
				<li>To start the miner using specific no. of threads (Ex. 2)<b>miner.start(2)</b></li>
				<li>To stop the miner: <b>miner.stop()</b></li>
				<li>To get the admin info. <b>admin</b></li>
				<li>To add a peer
					<ol>
						<li>Get the enode info of the other node (ex. <b>"enode://591def4c46746d7528837c1a6ef00741b1100c4ad03f0ff0d957991256f21aa947ba4282bf3aea89ed5a02aaf03d548b53bd102904cf8748d47244174ccda804@[::]:30304"</b> (Remove "?discport=0" if present))</li>
						<li>Replace @[::] with @privateIP (Ex. @172.28.143.12)></li>
						<li>Run <b>admin.addPeer("Final_IPC_END_POINT")</b></li>
						<li>Ex. <b>admin.addPeer("enode://7dfc49b8d71c17cd123f7e80f75a6deb38b8aa36ec021817772ed2a73f9a7dc9c0d7eb6d4fba9db39cec0d6ab9744492d1a3da710559f26ae5892ac977eb7128@172.28.210.141:30304")</b></li>
						<li>Run <b>admin</b> and check "peers" field inside it. If successful, you can see the other node entry inside it.</li>
					</ol>
				</li>
				<li>To unlock an account for specific secs(ex.300 secs): <b>personal.unlockAccount(eth.accounts[0],"{Your password}")</b></li>
				<li>To send ether from one account to other(Ex. account0 to last account): <b>eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[eth.accounts.length-1],value:web3.toWei(1,"ether")})</b></li>
				<li>To send ether using account address(Ex. your account0 to other peer account): <b>eth.sendTransaction({from:eth.accounts[0],to:"{address}",value:web3.toWei(1,"ether")})</b></li>
				<li>To see the pending transactions: <b>eth.pendingTransactions</b></li>
				<li>To see the latest Block number: <b>eth.blockNumber</b></li>
				<li>To see the data Inside a Block: <b>eth.getBlock({Block_no})</b></li>
				<li>To see the transaction detaild from Tx Hash <b>eth.getTransaction("{Tx Hash}");</b>
					<ul>
						<li>Ex. <b>eth.getTransaction("0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421")</b></li>
					</ul>
				</li>

				<li>To come out of the geth console: <b>exit</b></li>
			</ul>
		</li>
	</ol>	 
</div>
