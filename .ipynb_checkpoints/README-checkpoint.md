# Crowdsale With ERC20 Token
![ICO](https://miro.medium.com/max/4096/1*UAWdBaNLGkbmiB4NOBl0hQ.jpeg)

This Blockchain example utilizes the OpenZeppelin Solidity library to create an ERC20 token that is minted through a crowdsale contract.  The contract will allow users to send ETH and get back PUP, or PupperCoin, the hypothetical name of the company's token.  The contract mints the tokens automatically and distributes them to buyers in one transaction.  A real-world pre-production test is shown in which I deploy the crowdsale to the Kovan testnet.

---

# Contract Set-Up / Deployment:

## 1. Use Remix to create a .sol file and create a standard ERC20Mintable token:
- Use Standard ERC30Mintable and ERC30Detailed contracts from Open Zeppelin
- Hardcode 18 as the decimals parameter
- You don't need to hardcode the decimals, however since most use-cases match Ethereum's default, you may do so.
- After compiling your code, fill in the Name, Symbol and Initial_Supply for your token and deploy to your local chain using MetaMask

![first_contract](/Screenshots/first_contract.gif?raw=true)

## 2. Create a new .sol file to write the code for your Crowdsale:
- You will need to bootstrap the contract by inheriting the following OpenZeppelin contracts:
Crowdsale  
MintedCrowdsale  
CappedCrowdsale  
TimedCrowdsale  
RefundablePostDeliveryCrowdsale
- You will need to provide parameters for all of the features of your crowdsale, such as the name, symbol, wallet for fundraising, goal, etc. Feel free to configure these parameters to your liking.
- You can hardcode a rate of 1, to maintain parity with Ether units (1 TKN per Ether, or 1 TKNbit per wei). If you'd like to customize your crowdsale rate, follow the Crowdsale Rate calculator on OpenZeppelin's documentation. Essentially, a token (TKN) can be divided into TKNbits just like Ether can be divided into wei. When using a rate of 1, just like 1000000000000000000 wei is equal to 1 Ether, 1000000000000000000 TKNbits is equal to 1 TKN.
- Since RefundablePostDeliveryCrowdsale inherits the RefundableCrowdsale contract, which requires a goal parameter, you must call the RefundableCrowdsale constructor from your PupperCoinCrowdsale constructor as well as the others. RefundablePostDeliveryCrowdsale does not have its own constructor, so just use the RefundableCrowdsale constructor that it inherits.
- If you forget to call the RefundableCrowdsale constructor, the RefundablePostDeliveryCrowdsale will fail since it relies on it (it inherits from RefundableCrowdsale), and does not have its own constructor.
- When passing the open and close times, use now and now + 24 weeks to set the times properly from your PupperCoinCrowdsaleDeployer contract.
- Finally, deploy to your local chain using MetaMask












![OriginalDF](/Screenshots/OriginalDF.png?raw=true)
