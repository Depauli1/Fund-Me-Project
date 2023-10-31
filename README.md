# Fund-Me-Project

## Introducing FundMe

Designed with precision, FundMe simplifies the fundraising experience, offering a seamless platform where creators and backers converge for a shared vision of progress.
Here's what sets FundMe apart:

FundMe facilitates effortless fund collection by allowing users to securely contribute funds through our dedicated smart contract. 
With a user-friendly interface, backers can seamlessly transfer money, ensuring a hassle-free donation process.

At FundMe, we understand the importance of clarity in fundraising endeavors. 
Project creators can set minimum funding goals in USD, providing a defined target that backers can rally behind. 
This strategic approach ensures campaigns are purposeful and attainable, maximizing the chances of success.

Once the campaign achieves its funding objective, FundMe simplifies the fund withdrawal process. 
Creators can easily access the accumulated funds, ensuring timely and efficient execution of their projects. 
Our platform streamlines financial transactions, allowing creators to focus on bringing their visions to life.

Why Choose FundMe?

FundMe prioritizes the security of every transaction, implementing advanced blockchain technology to safeguard user funds and data.
We uphold transparency and accountability in every transaction. Backers can confidently support the project, knowing that their contributions are utilized purposefully and responsibly.
FundMe transcends geographical boundaries, connecting creators with a global community of supporters.
Together, we empower ideas to create meaningful change on a global scale.

# Getting Started

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (816

 ## Quickstart

```
git clone https://github.com/Depauli1/Fund-Me-Project
cd foundry-fund-me-f23
forge build
```

# Usage

## Deploy:

```
forge script script/DeployFundMe.s.sol
```

## Testing

I used this four tests when building the code.

1. Unit
2. Integration
3. Forked
4. Staging

```
forge test
```

or 

```
// Only run test functions matching the specified regex pattern.

"forge test -m testFunctionName" is deprecated. Please use 

forge test --match-test testFunctionName
```

or

```
forge test --fork-url $SEPOLIA_RPC_URL
```

### Test Coverage

```
forge coverage
```

# Deployment to a testnet or mainnet

1. Setup environment variables

You'll want to set your `SEPOLIA_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file, similar to what you see in `.env.example`.

- `PRIVATE_KEY`: The private key of your account (like from [metamask](https://metamask.io/)). **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
  - You can [learn how to export it here](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `SEPOLIA_RPC_URL`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com/?a=673c802981)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/).

2. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.

3. Deploy

```
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
```

## Scripts

After deploying to a testnet or local net, you can run the scripts. 

Using cast deployed locally example: 

```
cast send <FUNDME_CONTRACT_ADDRESS> "fund()" --value 0.1ether --private-key <PRIVATE_KEY>
```

or
```
forge script script/Interactions.s.sol --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast
```

### Withdraw

```
cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()"  --private-key <PRIVATE_KEY>
```

## Estimate gas

You can estimate how much gas things cost by running:

```
forge snapshot
```

And you'll see an output file called `.gas-snapshot`

# Formatting


To run code formatting:
```
forge fmt
```


# Thank you!
