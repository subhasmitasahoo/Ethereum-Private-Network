<h1 style="color: green;">Create a private Ethereum Network in local</h1>
<div>
	<ol>
		<li>Install and Update Homebrew
			<ul>
				<li>Install Homebrew: <b>ruby -e “$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"</b></li>
				<li><b>brew update</b></li>
				<li><b>brew upgrade</b></li>
			</ul>
		</li>
		<li>Install Ethereum
			<ul>
				<li><b>brew tap ethereum/ethereum</b></li>
				<li><b>brew install ethereum</b></li>
			</ul>
		</li>
		<li>Node creation
			<ul>
				<li>create a private folder e.g.: <b>mkdir privateEth</b></li>
				<li>Go inside the directory: <b>cd privateEth</b></li>
				<li>Create a genesis file: <b>touch genesis.json</b></li>
				<li>Copy the contents of genesis file from the github repository</li>
				<li>Instantiate the genesis block: <b>geth --datadir ./dataDir init ./genesis.json</b></li>
				<li>Start the node: <b>geth --datadir ./dataDir</b></li>
			</ul>
		</li>
		<li>Geth Console
			<ul>
				<li>Open a new console tab</li>
				<li>Start the geth console: <b>geth attach</b></li>
				<li>(Optional) If you want to attach to a specific IPC endpoint: <b>geth attach (ipc endpoint name)</b></li>
				<li>List accounts: <b>eth.accounts</b></li>
				<li>To see the default account: <b>eth.coinbase</b></li>
				<li>Balance of etherbase account: <b>eth.getBalance(eth.coinbase)</b></li>
				<li>Balance of any account(Here index is 0): <b>eth.getBalance(eth.accounts[0])</b></li>
				<li>To get the balance in ether: <b>web3.fromWei(eth.getBalance(eth.coinbase),"ether")</b></li>
				<li>To start the miner (This adds balance in etherbase account)<b>miner.start()</b></li>
				<li>To start the miner using specific no. of threads (Ex. 2)<b>miner.start(2)</b></li>
				<li>To stop the miner: <b>miner.stop()</b></li>
				<li>To unlock an account for specific secs(ex.300 secs): <b>personal.unlockAccount(eth.accounts[1],"{Your password}",300)</b></li>
				<li>To create an account <b>personal.newAccount()</b></li>
				<li>To send ether from one account to other(Ex. account0 to last account): <b>eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[eth.accounts.length-1],value:web3.toWei(1,"ether")})</b></li>
				<li>To see the pending transactions: <b>eth.pendingTransactions</b></li>
				<li>To come out of the geth console: <b>exit</b></li>
			</ul>
		</li>
	</ol>	 
</div>