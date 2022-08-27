<!DOCTYPE html>
<body>
<head> SOLANA TOKEN CREATINO </head>
<h1>## Latest Solana Token Creation, Naming & Updating (Step by Step Guide for Beginners) - July 2022</h1>

<a href="https://cutt.ly/KLVbCwF"><b>Reference Guide:</b></a>
<ul>
<li> Download & Install **Visual Studio Code: https://code.visualstudio.com/download </li>
<li>Download & Install **Latest Node.js: https://nodejs.org/en/download</li>
<li>Install **Npm ts node** from your terminal: npm install -g ts-node<br></li>
npm install -g typescript:
<li>Create a IPFS account on Pinata: https://pinata.cloud</li>
</ul>

## Step 2: Open Up Visual Studio Code

1. Create a folder on your machine
2. Open up the file from **VS Code**
3. Click on Terminal 
4. Install Solana CLI Tools based on your OS: [https://docs.solana.com/cli/install-solana-cli-tools](https://docs.solana.com/cli/install-solana-cli-tools)
5. After installed, Install these 3 command lines one after the order. You might need to have the latest node.js installed and typescript for it to run.

```jsx
npm install @metaplex-foundation/mpl-token-metadata --save
```

```jsx
npm install @solana/web3.js --save
```

```jsx
npm install @project-serum/anchor --save
```

1. Now, the next thing is to create 2 customized wallets **(Vanity Wallet).** The first one is for our **Token Address** and the second one for our **Main Address.** You can customize the name. For instance, if my token name is **Thee Token**, I can customize my token address name to start with something like the**.** So, I can change the name to **the.** The 1 means the number of wallets to generate. Leave it as 1

```jsx
solana-keygen grind --starts-with name:1
```

1. Create another wallet that will be for the **Main Wallet.** Change the name as well to something you can recognize. For instance, **vic**

```jsx
solana-keygen grind --starts-with name:1
```

1. Now, Copy and save those 2 wallet addresses. You can confirm it on **Solana Explorer**

```jsx
https://explorer.solana.com/
```

1. Now, we have to config for either **Solana Devnet or Mainnet. NB:** You have to change my-keypair.json to the Main wallet address you create earlier. In my case, vic… ending with .json

```jsx
solana config set --url https://api.devnet.solana.com --keypair my-keypair.json
```

```jsx
solana config set --url https://api.mainnet-beta.solana.com --keypair my-keypair.json
```

1. If you’ve config for Devnet, airdrop some free SOL. **For Mainnet, send real SOL to the Main Wallet.** In my case, my token address starts with vic

```jsx
solana airdrop 2
```

1. Check the Main Wallet on Solana Explorer to confirm
2. Now, Let’s create our token. If you’re creating for NFT, leave it as 0. For token, you can add your token decimals. For instance, 18. 

**NOTE:** You need to add the token-address.json here not the main-address.json. In my case, my token address is (the…..json)

```jsx
spl-token create-token --decimals 18 GRPYwHSbVNHotuSSgk9FShwkwKtKVSm3RqZi1Ui7JzXS.json
```

1. Now, we need to create the Token Account. Change the **(token address)** in the code below to your token address. 

*Copy & save the account address*

```jsx
spl-token create-account (token address)
```

1. The next thing is to mint our token. Run the following command. Make sure to change (token address) and (Number of tokens)

```jsx
spl-token mint (token address) (Number of tokens)
```

1. **WE’VE SUCCESSFULLY CREATED OUR TOKEN.** Confirm it on Solana Explorer
2. Now, the next thing is for us to Register our Token by adding our ***Name, Symbol, and Image*** to it.
3. On your VS Code, create a new file and call it **first.ts.** Now, paste the following commands inside. This is a Typescript file. 

**NOTE:** Make sure metaplex foundation and ts-node are installed on your machine and you’re using the latest version of Node.js (to avoid error).

You can update your Node.js with this command line: npm install latest-version OR npm install -g npm@latest
