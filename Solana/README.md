<!DOCTYPE html>
<body>
<head> SOLANA TOKEN CREATION </head>
<h1>Latest Solana Token Creation, Naming & Updating (Step by Step Guide for Beginners) - July 2022</h1>

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

- Now, the next thing is to create 2 customized wallets **(Vanity Wallet).** The first one is for our **Token Address** and the second one for our **Main Address.** You can customize the name. For instance, if my token name is **Thee Token**, I can customize my token address name to start with something like the**.** So, I can change the name to **the.** The 1 means the number of wallets to generate. Leave it as 1

```jsx
solana-keygen grind --starts-with name:1
```

- Create another wallet that will be for the **Main Wallet.** Change the name as well to something you can recognize. For instance, **vic**

```jsx
solana-keygen grind --starts-with name:1
```

- Now, Copy and save those 2 wallet addresses. You can confirm it on **Solana Explorer**

```jsx
https://explorer.solana.com/
```

- Now, we have to config for either **Solana Devnet or Mainnet. NB:** You have to change my-keypair.json to the Main wallet address you create earlier. In my case, vic… ending with .json

```jsx
solana config set --url https://api.devnet.solana.com --keypair my-keypair.json
```

```jsx
solana config set --url https://api.mainnet-beta.solana.com --keypair my-keypair.json
```

- If you’ve config for Devnet, airdrop some free SOL. **For Mainnet, send real SOL to the Main Wallet.** In my case, my token address starts with vic

```jsx
solana airdrop 2
```

- Check the Main Wallet on Solana Explorer to confirm
- Now, Let’s create our token. If you’re creating for NFT, leave it as 0. For token, you can add your token decimals. For instance, 18. 

**NOTE:** You need to add the token-address.json here not the main-address.json. In my case, my token address is (the…..json)

```jsx
spl-token create-token --decimals 18 GRPYwHSbVNHotuSSgk9FShwkwKtKVSm3RqZi1Ui7JzXS.json
```

- Now, we need to create the Token Account. Change the **(token address)** in the code below to your token address. 

*Copy & save the account address*

```jsx
spl-token create-account (token address)
```

- The next thing is to mint our token. Run the following command. Make sure to change (token address) and (Number of tokens)

```jsx
spl-token mint (token address) (Number of tokens)
```

- **WE’VE SUCCESSFULLY CREATED OUR TOKEN.** Confirm it on Solana Explorer
- Now, the next thing is for us to Register our Token by adding our ***Name, Symbol, and Image*** to it.
- On your VS Code, create a new file and call it **first.ts.** Now, paste the following commands inside. This is a Typescript file. 

**NOTE:** Make sure metaplex foundation and ts-node are installed on your machine and you’re using the latest version of Node.js (to avoid error).

You can update your Node.js with this command line: npm install latest-version OR npm install -g npm@latest

1. Go to Line 18 in the code and change to your **main wallet** address

```jsx
const myKeypair = loadWalletKey("vicZqzb2mXjN5x68kgePx9Gh8sF9wQ3x8UnGAxJfid9.json")
```

1. Go to Line 20 in the code and change it to your **token address** without the .json

![Screenshot 2022-07-19 at 11.00.43 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/02aded32-cabb-4031-b028-e90687e4645a/Screenshot_2022-07-19_at_11.00.43_AM.png)

1. Go to Line 40 in the code and Change to your Token Name, Token Symbol
2. Go to Line 60 and change to Devnet or Mainnet

![Screenshot 2022-07-19 at 11.02.56 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/55e368c0-b319-4c1f-b09c-6c5640770e40/Screenshot_2022-07-19_at_11.02.56_AM.png)

1. Now, we need to generate the URI. Go to your **pinata account** and upload your image first. 
2. Create a new file in VS code and call it **metadata.json**. Paste the code below inside the metadata.json file. 

```jsx
{
    "name": "Victor Token",
    "symbol": "$VIC",
    "description": "Thee Token is for tea lovers.",
    "image": "https://gateway.pinata.cloud/ipfs/QmRbqdCYCEJtrhCViqVsmUfGvNk2QYMP99dJw1sJm5j88L"
  }
```

1. Update your token name, symbol, and description, and change the image to the token logo URL generated from pinata
2. Now, upload the **metadata.json** file to Pinata Cloud
3. Copy your URI and paste it into Line 42 in the **first.ts** file (which is our original file)
4. Now, Run this command

```jsx
ts-node first.ts
```

1. **CONGRATULATIONS!!!** Our Token Is Successfully Registered Now 😍😍😍 Check and confirm it on Solana Explorer.

# NOW, PROBABLY YOU WANT TO UPDATE YOUR TOKEN INFORMATION

1. Create a second.ts file in VS code
2. Copy and paste this line of code below

```jsx
import * as mpl from "@metaplex-foundation/mpl-token-metadata";
import * as web3 from "@solana/web3.js"
import * as anchor from '@project-serum/anchor'

export function loadWalletKey(keypairFile: string): web3.Keypair {
    const fs = require("fs");
    const loaded = web3.Keypair.fromSecretKey(
        new Uint8Array(JSON.parse(fs.readFileSync(keypairFile).toString())),
    );
    return loaded;
}

const INITIALIZE = false;

async function main() {
    console.log("Let's name some tokens");

    const myKeypair = loadWalletKey("BEDM9mz8Rne3yP3UDpqjixmxUhMLRJWzh5S2YYnixTTX.json")
    console.log(myKeypair.publicKey.toBase58())
    const mint = new web3.PublicKey("XYZxvq4uFxyhi9La3Ba63fpmkbkeCYaWVyN2vzVDSRc")

    const seed1 = Buffer.from(anchor.utils.bytes.utf8.encode("metadata"));
    const seed2 = Buffer.from(mpl.PROGRAM_ID.toBytes());
    const seed3 = Buffer.from(mint.toBytes());

    const [metadataPDA, _bump] = web3.PublicKey.findProgramAddressSync([seed1, seed2, seed3], mpl.PROGRAM_ID);

    const accounts = {
        metadata: metadataPDA,
        mint,
        mintAuthority: myKeypair.publicKey,
        payer: myKeypair.publicKey,
        updateAuthority: myKeypair.publicKey,
    }

    const dataV2 = {
        name: "Gizmooooo Coin",
        symbol: "$GIZMOOOOO",
        uri: "https://5ccwmdhforuyru3bwywsd2ilylllfwizxryzdjcvlyteshacee.arweave.net/6IVmDOV0aYjTYbYtIekLwtay2Rm8cZ-GkVV4mSRwCIY",
        // we don't need that
        sellerFeeBasisPoints: 0,
        creators: null,
        collection: null,
        uses: null,

    }

    let ix;
    if (INITIALIZE) {
        const args = {
            createMetadataAccountArgsV2: {
                data: dataV2,
                isMutable: true
            }
        };
        ix = mpl.createCreateMetadataAccountV2Instruction(accounts, args);
    } else {
        const args = {
            updateMetadataAccountArgsV2: {
                data: dataV2,
                isMutable: true,
                updateAuthority: myKeypair.publicKey,
                primarySaleHappened: true
            }
        };
        ix = mpl.createUpdateMetadataAccountV2Instruction(accounts, args)
    }

    const tx = new web3.Transaction();
    tx.add(ix);
    const connection = new web3.Connection("https://api.devnet.solana.com");
    const txid = await web3.sendAndConfirmTransaction(connection, tx, [myKeypair]);
    console.log(txid);

}

main()
```

1. Update the Info like the first step (Name, Symbol & metadata URI)
2. Run this command in terminal

```jsx
ts-node second.ts
```

1. Check Solana Explorer. Your token info will be automatically updated.

# SOME QUESTIONS YOU MIGHT HAVE

- **Why Do I Receive this warning:** **Warning! Token names and logos are not unique. This token may have spoofed its name and logo to look like another token. Verify the token's mint address to ensure it is correct.**
    
    You can check the Solana Explorer source code to see what triggers this warning [https://github.com/solana-labs/solana/blob/master/explorer/src/pages/AccountDetailsPage.tsx#L210=](https://github.com/solana-labs/solana/blob/master/explorer/src/pages/AccountDetailsPage.tsx#L210=)
    
    Tokens are considered verified only if part of the [spl-token-registry](https://www.npmjs.com/package/@solana/spl-token-registry). However, this repository has recently been deprecated in favor of the Metaplex token metadata standard.
    
- **Can I still mint more tokens after creating a token?**
    
    Yes, definitely. You can mint more tokens. The only way you may not be able to mint more tokens in the future is if you’ve disabled minting on your account using this command: spl-token authorize {token address} mint --disable Understand that this process is irreversible and will change your token from ***Circulating supply to Max supply when you check on Solana Explorer.** So only use that command line if you’re sure you don’t want to mint any new tokens in future.*
    
- **How can I give permission and ownership to the token assuming am creating it for a client?**
    
    You can give your clients permission by sharing them access to the wallet keypair you generate during the time of creating the wallet. With that, they can have full ownership of the token wallet and main wallet.
