**Exploring smart contracts working and their security challenges**

In this digital age, trust is often facilitated by intermediaries. However the emergence of blockchain technology has introduced a new era of this decentralised world. The heart of this revolution lies in **Smart contracts, **self - executing agreements encoded on blockchain ensuring transparency, efficiency and independance.

In this article, we?ll look at -

1. Introduction to smart contracts

2. How smart contract works

3. What makes smart contracts secure

4. Security challenges in smart contracts

1. **Introduction to smart contracts**

	In 2013, ethereum introduced a core innovation by enabling developers to create small pieces of code, referred to as smart contracts, that could be deployed to ethereum network to run independently of their creators.

In ethereum, these smart contracts are written in a high-level programming language **Solidity, **designed to run on EVM(Ethereum Virtual Machine). 

In smart contracts, the terms of agreements are directly written in the form of code. These contracts are said to be self-executing contracts because they define a set of rules or ?contract? which executes automatically and enforces the terms of agreement when predetermined conditions are met. Smart contracts always function identically once they are deployed on any network.

**Key components of a smart contract-**

- **Participants - **These entities engage with the contract including individuals, systems or other contracts.

- **State - **State  denotes the current condition of a smart contract which changes as participants interact with the contract.

- **Functions - **These are specific operations or actions that can be executed by contracts.These functions are called by participants and have the ability to change the state of smart contracts.

- **Rules - **These are the predefined conditions that govern the operations and behaviour of the contract. Embedded with the contract?s code, rules must be met for the functions to be executed.

For a better understanding of how a smart contract looks like, let?s see an example -

Suppose a smart contract which is used to store the bank balances of people associated with their account numbers. The functionalities will be deposit and withdrawal of money.

**State** - to store the balances along with account numbers.

**Functions** - to perform deposit and withdrawal

This simple smart contract will look like -

![](/images/Yag_Image_1.png)

- **How smart contract works**

Smart contracts operate autonomously on a blockchain, executing predefined actions when triggered by specific conditions. They eliminate the need for intermediaries, ensuring transparent, efficient, and tamper-proof transactions. Once deployed, smart contracts cannot be altered, enhancing security and reliability while streamlining processes and reducing costs.

Smart contracts function as a digital agreement secured by blockchain technology. It contains specific instructions and conditions written in code, which must be precisely followed to activate the contract's terms.

Additionally, smart contracts may incorporate time limits, introducing deadlines for compliance. Each smart contract possesses a unique address on the blockchain, enabling interaction by participants who possess the contract's address and provided it has been published on the network.

![](/images/ogl_Image_2.png)

                  Image from - [https://www.geeksforgeeks.org/smart-contracts-in-blockchain/](https://www.geeksforgeeks.org/smart-contracts-in-blockchain/)

**Identify Agreement:** Initially, involved parties recognize potential collaborative ventures and establish desired outcomes, whether it involves business operations or asset transactions.

**Set Conditions:** Smart contracts come into play either through manual initiation by participants or automatically triggered by specific conditions, such as market fluctuations or predefined events.

**Code Business Logic:** Programmers develop the underlying code that encapsulates the contract's logic, dictating the actions to be taken once the predetermined conditions are met.

**Encryption and Blockchain Technology:** Robust encryption mechanisms safeguard the communication channels, while the utilisation of blockchain technology ensures transparency, security, and immutability of the contract's data.

**Execution and Processing:** Upon consensus among the involved parties, the smart contract's code is executed, carrying out the specified actions. The outcomes of these actions are then recorded on the blockchain for compliance and verification purposes.

**Network Updates:** Following the execution of the smart contract, all nodes within the blockchain network update their ledgers to reflect the latest state of the contract. This ensures that the recorded data remains immutable and transparent, with any changes or updates appended to the existing ledger.

- **What makes smart contracts secure**

Smart contracts are considered secure due to several reasons -

- **Immutability:**

Once deployed on the blockchain, smart contracts cannot be altered or tampered with. This immutability ensures that the terms and conditions of the contract remain unchanged, providing a reliable and secure framework for transactions.

<span style="text - decoration: underline;">Example </span>- a crowdfunding smart contract locks in the rules for disbursing funds to project creators and cannot be altered by any party once contributions have been made.

- **Decentralisation:**  

Smart contracts operate on a decentralised network of nodes, meaning there is no single point of failure. This decentralised nature reduces the risk of attacks or manipulation by malicious actors, enhancing security.

<span style="text - decoration: underline;">Example - </span> In a decentralised exchange (DEX) smart contract, trades are executed directly between users without the need for a centralised authority. This eliminates the risk of manipulation by a single entity.

- **Cryptography:**

Smart contracts leverage cryptographic techniques to secure transactions and communications. Encryption ensures that data transmitted between parties remains confidential and cannot be intercepted or modified by unauthorised parties.

<span style="text - decoration: underline;">Example - </span> an escrow smart contract might use digital signatures to authenticate parties involved in a transaction.

- **Consensus mechanisms:**

Blockchain networks rely on consensus mechanisms, such as Proof of Work (PoW) or Proof of Stake (PoS), to validate transactions and ensure agreement among network participants. These consensus mechanisms contribute to the overall security and integrity of smart contracts by preventing fraudulent or malicious activities.

<span style="text - decoration: underline;">Example - </span> In a Proof of Stake (PoS) blockchain network, smart contracts are validated by participants who have staked their cryptocurrency. This ensures agreement among network participants without the need for a central authority.

- **Transparency:**

The transparent nature of blockchain technology allows all transactions and contract executions to be publicly recorded and verified by network participants. This transparency enhances trust and accountability, making it more difficult for malicious activities to go unnoticed.

<span style="text - decoration: underline;">Example -</span> Consider a supply chain management smart contract where each step in the production and distribution process is recorded on the blockchain. This transparency allows consumers to verify the origin and authenticity of products.

- **Permissionless access:**

In many blockchain networks, smart contracts can be accessed and interacted with by anyone on the network, without the need for permission from a central authority. This permissionless access increases the network's resilience and reduces the risk of censorship or control by centralized entities.

<span style="text - decoration: underline;">Example -</span> In a decentralized lending platform, borrowers and lenders can interact directly through smart contracts without needing approval from a central authority. This allows for greater accessibility and inclusivity in financial services.

- **Smart contracts security challenges -**

In recent years, smart contracts have emerged as a powerful tool for automating and executing agreements in a decentralised and tamper-proof manner. These self-executing contracts, powered by blockchain technology, promise transparency, efficiency, and autonomy. However, alongside their potential benefits, smart contracts also introduce unique security challenges. From vulnerabilities in code to the irreversible nature of blockchain transactions, ensuring the security of smart contracts has become paramount.

Below given is the list of potential security challenges for a smart contract.

Let?s see them one by one -

![](/images/Esd_Image_3.png)

- **Reentrancy attack -**

This form of attack poses a severe threat as it can result in the complete depletion of ether from a vulnerable smart contract and is very simple to unintentionally trigger.

Reentrancy attacks exploit two fundamental characteristics of Solidity:

1. Smart contracts execute commands sequentially, meaning they must wait for each line to complete before moving on to the next.

2. Smart contracts can interact with external, potentially untrusted contracts and pause execution to await the outcome before proceeding.

****

**For example: **In situations where a vulnerable contract A initiates an external call to another untrusted contract B, there exists a risk that contract B could be manipulated to execute a recursive call back to contract A maliciously. If the initial call from contract A to contract B involves transferring any amount of Ether, this recursive loop could deplete all resources from contract A before the function completes.

Consider this straightforward illustration:

?-------------------------------------------------------------------------------------------------------------

contract A {

function withdraw() external {

uint256 amount = balances[msg.sender];

(bool success, ) = msg.sender.call.value(amount)("");

require(success);

balances[msg.sender] = 0;

}

}

?-------------------------------------------------------------------------------------------------------------

Properly utilizing the ?Checks-Effects-Interactions? pattern can mitigate this vulnerability.

Implementing the ?Checks-Effects-Interactions? pattern ensures that all state changes are made before interacting with external contracts, reducing the risk of reentrancy attacks.

- **Denial of service**

A Denial of Service (DoS) attack is initiated when a malicious entity deliberately interferes with the typical operation of a system, causing it to become inaccessible to its legitimate users.

In the context of Solidity smart contracts, a DoS attack exploits weaknesses to deplete essential resources like gas, CPU cycles, or storage, thereby incapacitating the contract and preventing its intended functionality. Denial of service attack in smart contracts can be done in multiple ways like -



	**i.  Gas exhaustion attack:** 

Solidity smart contracts operate on the Ethereum Virtual Machine (EVM), where each  operation consumes a specific amount of gas. This characteristic is exploited by malicious actors who craft transactions or contract functions demanding an excessive amount of gas to execute. Consequently, gas resources are depleted, causing the contract to halt and denying legitimate users access to its services.

Here is a code snippet that show how it is done

?-------------------------------------------------------------------------------------------------------------

//example vulnerable code

function executeTransaction(uint[] memory values) public {

for(uint j = 0; j < values.length; j++) {

// expensive computation

}

}

?-------------------------------------------------------------------------------------------------------------

To defend against gas exhaustion attacks, it is crucial to optimize your contract's code to minimize gas consumption. Employ gas-efficient algorithms and carefully consider gas limits when designing functions.

	**ii.  Reentrancy attack**

A reentrancy attack occurs when a malicious actor exploits a vulnerability in a contract to repeatedly execute certain actions within the same function call. This unauthorized action can lead to accessing sensitive data or funds in an unintended manner.

The DAO hack of 2016 is a well-known example of a reentrancy attack, where an attacker was able to drain funds from the DAO contract by repeatedly withdrawing funds before the contract's balance was updated. Employing the "Checks-Effects-Interactions" pattern, which involves performing checks first, then updating internal state, and finally interacting with external contracts or sending funds, can help mitigate this vulnerability by ensuring that interactions are performed in a secure and predictable manner.

?-------------------------------------------------------------------------------------------------------------

//example vulnerable code

mapping(address => uint) userBalances;

function performWithdrawal() public {

uint withdrawalAmount = userBalances[msg.sender];

require(withdrawalAmount > 0, "Insufficient balance");

userBalances[msg.sender] = 0;

(bool transferSuccess, ) = msg.sender.call{value: withdrawalAmount}("");

require(transferSuccess, "Failed to transfer funds");

}

?-------------------------------------------------------------------------------------------------------------

This code is vulnerable because it allows for reentrancy attacks, where malicious actors can repeatedly call the withdraw function before the balance update, resulting in unauthorized fund withdrawals. Additionally, the use of call to transfer funds without proper checks can lead to unexpected behaviour, such as sending funds to malicious contracts.

	**iii.  Block gas limit attack**

In Ethereum, each block has a gas limit, constraining the cumulative gas consumption of all transactions within it. Malicious actors exploit this limitation by crafting transactions that consume an extraordinary amount of gas, thereby obstructing the inclusion of legitimate transactions in the same block. While this attack does not directly target the contract, it disrupts the regular operation of the blockchain.

?-------------------------------------------------------------------------------------------------------------

/ Example vulnerable code

function consumeAllGas() public {

uint i = 0;

while (true) {

i++;

}

}

?-------------------------------------------------------------------------------------------------------------

To mitigate block gas limit attacks, it's crucial to design your smart contract functions with reasonable gas requirements and optimize your code to be efficient, avoiding infinite loops and unnecessary computational complexity. By carefully managing gas consumption, you reduce the risk of encountering situations where transactions consume excessive gas, potentially exceeding the block gas limit. Additionally, optimizing your code enhances the overall performance and scalability of your smart contracts, ensuring smoother operation within the constraints of the blockchain network.



- **Oracle manipulation Attacks**

Oracle attacks in blockchain occur when malicious actors exploit the dependency of smart contracts on external data sources, known as oracles, to manipulate contract execution or gain unauthorized access to sensitive information.

Oracles serve as bridges between smart contracts and real-world data, providing crucial information like prices for decentralized applications (dApps) to operate effectively.

However, attackers can manipulate oracle data to deceive smart contracts into executing unintended or malicious actions. This manipulation can result in undesirable consequences, including financial losses or security breaches, undermining the reliability and integrity of the blockchain ecosystem.

Below are some point which can cause this type of attack -

1. Centralization of Oracles: If the oracle providing data to the smart contract is centralized, it becomes a single point of failure susceptible to manipulation or compromise by malicious actors.

2. Data Source Reliability: If the data source feeding the oracle is unreliable or untrustworthy, it increases the risk of inaccurate or manipulated information being provided to the smart contract.

3. Lack of Data Verification: Smart contracts often trust the data provided by oracles without verifying its authenticity or integrity, leaving them vulnerable to manipulation.

4. Delayed or Incorrect Data Feeds: Delays or inaccuracies in data feeds from oracles can lead to misinformed decisions by smart contracts, creating opportunities for manipulation.

Preventing oracle manipulation attacks involves a combination of strategies:

1. By using multiple oracles from different data sources

2. Time-Weighted Average Prices (TWAPs)

3. Using Decentralized Oracle Networks (like chainlink)

4. Implementing slippage protection

- **Frontrunning**

Smart contracts and transactions become publicly visible as soon as they are submitted to the network as pending transactions, even before confirmation on the blockchain. These pending transactions are shared across the Ethereum network in mempools, allowing miners to prioritize transactions with higher gas fees. This transparency exposes the intended outcomes of smart contracts to all users for a period before confirmation.

This visibility can lead to front-running attacks, where malicious actors copy and submit transactions with higher gas fees to exploit arbitrage opportunities before the original transaction is processed. In many cases, miners themselves carry out these attacks, resulting in a phenomenon called MEV (miner extractable value), which can generate significant profits daily.

**For Example:** Alice submits a transaction to execute an arbitrage trade using a smart contract, offering a transaction fee of 0.05 ETH. Before Alice's transaction is confirmed, Bob spots it in the mempool, copies the trade, and submits it with a higher fee of 0.06 ETH. Miners prioritize Bob's transaction, executing the arbitrage trade before Alice's, resulting in Bob profiting from the opportunity instead. This illustrates how front-running attacks exploit the visibility of pending transactions to gain an advantage in decentralized exchanges.

- **Timestamp dependance**

Because of the decentralized structure of the blockchain network, synchronizing the precise time between nodes presents one of the most challenging issues for blockchain technology. Nonetheless, in the process of developing smart contracts, the necessity of determining the current time becomes unavoidable, particularly considering that most smart contract development languages are Turing complete.

The timestamp dependency vulnerability occurs when a smart contract relies on the timestamp value generated by the node and compares it to a future time value that is less than 900 seconds away.

Let?s see a simple smart contract of lottery that shows this vulnerability-

?-------------------------------------------------------------------------------------------------------------

pragma solidity ^0.8.0;

contract VulnerableLottery {

address public owner;

uint public lastWinnerTimestamp;

constructor() {

owner = msg.sender;

}

function enterLottery() public payable {

require(msg.value == 1 ether, "Please send exactly 1 ether to enter the lottery.");

lastWinnerTimestamp = block.timestamp; // Record the timestamp of the last entry

}

function pickWinner() public {

require(msg.sender == owner, "Only the owner can pick a winner.");

require(block.timestamp >= (lastWinnerTimestamp + 900), "Cannot pick winner yet."); // Check if 15 minutes have passed

// Select winner and transfer prize

address payable winner = payable(address(uint160(uint(keccak256(abi.encodePacked(block.timestamp, block.difficulty, msg.sender)))) % 2)); // Pseudo-random winner for demonstration purposes

winner.transfer(address(this).balance);

}

}

?-------------------------------------------------------------------------------------------------------------

In this vulnerable lottery contract:

- Participants enter the lottery by sending exactly 1 ether.

- The enterLottery function records the timestamp of the last entry.

- The pickWinner function allows the owner to pick a winner after 15 minutes (900 seconds) have passed since the last entry. However, this condition is based on the timestamp generated by the node, which can be manipulated by miners.

- The winner is selected pseudo-randomly for demonstration purposes.

- **Griefing**

Griefing attacks target vulnerabilities in smart contracts, particularly in their business logic, aiming to disrupt the system's operation without yielding direct profit for the attackers. Despite not benefiting financially, these attacks can significantly impair the functionality of the smart contract system. Griefing attacks are often deployed to create disruption, either generally or during critical moments, within the system.

**For example-**

?-------------------------------------------------------------------------------------------------------------

mapping(address => uint) public balances;

function deposit() public payable {

balances[msg.sender] += msg.value;

}

function withdraw(uint amount) public {

require(balances[msg.sender] >= amount, "Insufficient balance");

balances[msg.sender] -= amount;

payable(msg.sender).transfer(amount); // Transfer funds to the caller

}

function attack(address target) public payable {

// Perform a griefing attack by repeatedly withdrawing funds

for (uint i = 0; i < 10; i++) {

(bool success, ) = target.call{value: 1 ether}("");

require(success, "Attack failed");

}

}

?-------------------------------------------------------------------------------------------------------------

In this example-

- Users can deposit funds into their account using the deposit function.

- They can withdraw funds from their account using the withdraw function, which transfers the specified amount of Ether to the caller.

- The attack function represents the griefing attack. It repeatedly calls a target contract's fallback function and sends 1 ether each time. This can result in the target contract running out of gas or encountering other issues due to the repeated transactions, disrupting its normal operation.

- **Overflow & Underflow**

In Solidity, a common attack involves exploiting underflows in unsigned integers, which can lead to unexpected behaviour in smart contracts.

Solidity smart contracts use a 256-bit word size, allowing for approximately 4.3 billion possible values. When an unsigned integer is decremented from 0, it wraps around to the maximum value. Malicious actors can exploit this by manipulating a smart contract to record a zero balance for an address and then attempting to send 1 unit of Ether. This causes the address's balance to wrap around to the maximum value, falsely inflating it to 4.3 billion Ether. Subsequent withdrawals from this address can then drain the smart contract of funds. To mitigate this vulnerability, it's recommended to use Solidity version 0.8 or higher, which includes automatic checks for overflows and underflows.

- **Forcefeeding**

One aspect to care about any smart contract that manages value is its accounting mechanism. Any errors in your financial tracking can result in complications.

Force feeding represents an attack targeting the accounting system of a smart contract by forcibly injecting Ether value into the contract. It is typically advised to refrain from utilizing a smart contract's balance for direct equality comparisons, as they can be compromised through a force feeding attack.

An attacker can forcefully send Ether in three ways. They are as follows:

1. Utilizing the "selfdestruct" function: When the "selfdestruct" function is invoked within a smart contract, the bytecode and storage associated with the contract are eradicated, and the Ether contained within the contract is forcibly transferred to a designated address, regardless of whether the address is capable of accepting Ether.

2. Deterministic Deployments: Smart contract addresses are derived from the keccak hash of the sender's address and nonce encoded via recursive length prefix (RLP). It is possible to send Ether to a contract address even prior to its deployment if its address is known.

3. Block rewards and coinbase: Should an attacker operate as a miner, they can designate the contract's address as their block coinbase, resulting in rewards (Ether) being directed to the contract irrespective of its ability to receive Ether.
