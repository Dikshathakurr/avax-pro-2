# Avax-pro-2

# Overview
This project makes use of Avalanche HyperSDK to build a custom subnet designed for particular blockchain features, including token creation and transfer.HyperSDK enables us to create a custom virtual machine for a blockchain, providing full control over its rules and functionality. This allows our startup to design a tailored blockchain solution for minting and transferring tokens, as well as managing asset trading. With HyperSDK, you achieve the flexibility and customization needed to meet your specific needs and gain a competitive edge.


#Note: I am unable to push my files from vs, so i zipped all the files and uploaded them as tokenvm . 

# Table of Contents

##  Description

1) Installation
2) Configuration
3) Running Your Subnet
4) Interacting with Your Subnet
5) Closing Your Subnet
6) License
7) Author

# Description

Description consts/consts.go contains the constants that is accessible across the hyperVM. The HRP, Name, and Symbol constants define information about the TokenVM, including its Human-Readable Part (HRP), name, and symbol.It lets us build a custom blockchain with specific rules, allowing you to mint and transfer tokens and manage asset trading. This helps your startup create a unique and competitive solution.

```bash
const (
	// TODO: choose a human-readable part for your hyperchain
	HRP = "avaxproject"
	// TODO: choose a name for your hyperchain
	Name = "avalanche"
	// TODO: choose a token symbol
	Symbol = "Avn"
)
```

This code is added in the consts/consts.go.

registry/registry.go contains the action that will be performed in the terminal during interaction.

```bash
// TODO: register action: actions.CreateAsset
consts.ActionRegistry.Register(&actions.CreateAsset{}, actions.UnmarshalCreateAsset, false),
// TODO: register action: actions.MintAsset
consts.ActionRegistry.Register(&actions.MintAsset{}, actions.UnmarshalMintAsset, false),
```

This code is added in registry/registry.go

# Steps of Execution :

This project is execute on WSl on windows and GO installed inside wsl.

1.run git clone https: ` https://github.com/Dikshathakurr/avax-pro-2.git`

2.run cd dikshaaa

3.Github is not allowing me to upload the files due to large no of files so I added the zip file. 

4.Extract the Avalanche hyperSDK project

5.cd '.\Avalanche hyperSDK project' 

6.In terminal run command MODE="run-single" ./scripts/run.sh and this will start our machine with 1 subnet and for 2 subnet run ./scripts/run.sh. after this command output will look like.

# Installation
To run this project, follow these steps:

1. GO Installation
Ensure Go is installed on your system. If not, follow the instructions from the official Go website.

2. Clone the Repository
Clone the project repository from GitHub:
```bash
git clone https://github.com/Metacrafters/tokenvm
cd tokenvm
```

3. Normalize Dependencies
Run go mod tidy to ensure all dependencies are correctly set up in your project folder in vs linked with wsl:

```bash
go mod tidy
```

# Configuration in the files
Set up the project constants as necessary:

1) Constants Configuration: Open `consts/consts.go} and add any variables or constants that are needed for your project.

2) Action Registration: Register custom actions such as Create_Asset and Mint_Asset} in registry/registry.go} if you haven't previously. By doing this, you can make sure that your custom actions may be executed on your subnet.

# Running Your Subnet
Start your subnet locally using the provided scripts:

1) Set Path for Go: Ensure Go is on your path:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
```
2)Run Scripts: Execute the following scripts to start your subnet:

```bash
MODE="run-single" ./scripts/run.sh
./scripts/build.sh
```

If you encounter permission issues, use:

```bash
bash ./scripts/run.sh
bash ./scripts/build.sh

```

# Interacting with Your Subnet
After starting your subnet, interact with it using the demo keys provided:

1) Load Demo Private Key:

```bash
./build/token-cli key import demo.pk
./build/token-cli chain import-anr

```

This step prepares your environment to interact with your local Avalanche network.

2) Execute Actions: Refer to the README or demo scripts for instructions on how to interact with your custom subnet. Examples include creating tokens, transferring them, and managing custom functionalities. So on terminal basically what to do

# Mint and Trade
Step 1: Create Your Asset
First up, let's create our own asset. You can do so by running the following command from this location:

```bash
./build/token-cli action create-asset
```

When you are done, the output should look something like this:

```bash
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 25vjnj2cAvnh6A5p31ZCUYXPCRCSEpMAL 27Ek0SP2doca833V 
assetID: zima3162brgGl@pBqp7goMir-2H76M6nYzwWE.TAUt6u5moQtJpp
metadata: MarioCoin supply: 0
recipient: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
amount: 500
continue (y/n): y
✅ txID: X1E5CVFgFFgniFyWcj5wweGg66TyzjK2bMWWTzFwJcwFYkF72

```
txID is the assetID of your new asset.

The "loaded address" here is the address of the default private key (demo.pk). We use this key to authenticate all interactions with the tokenvm.

# Step 2: Mint Your Asset
After we've created our own asset, we can now mint some of it. You can do so by running the following command from this location:

```bash
./build/token-cli action mint-asset
```
When you are done, the output should look something like this (usually easiest just to mint to yourself).

```bash
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 25vjnj2cAvnh6A5p31ZCUYXPCRCSEpMAL 27Ek0SP2doca833V 
assetID: zima3162brgGl@pBqp7goMir-2H76M6nYzwWE.TAUt6u5moQtJpp
metadata: MarioCoin supply: 0
recipient: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
amount: 500
continue (y/n): y
✅ txID: X1E5CVFgFFgniFyWcj5wweGg66TyzjK2bMWWTzFwJcwFYkF72
```

# Closing Your Subnet
To stop your local Avalanche network, run:
```bash
killall avalanche-network-runner
```

# License

MIT License

# Author

@Diksha Thakur
