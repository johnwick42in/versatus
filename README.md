# A Step by Step guide to Deploy A Program & create Fungible & Non-Fungible tokens on Versatus backed by Jump, Big Brain Holdings, NGC Ventures & more...
![img](https://pbs.twimg.com/profile_banners/1465798967657209857/1695224624/1500x500)

About Me : Just a guy | [X](https://x.com/@bigiley) | [Telegram](https://t.me/johnw1k) | [Farcaster](https://warpcast.com/johnwick69)

Projects Official links
   - Website : http://versatus.io/
   - Twitter : https://twitter.com/VersatusLabs
   - Discord : https://discord.gg/versatus

## Steps for Downloading Versatus Wallet Extension.
   - Go to [this link](https://itero.plasmo.com/ext/omkbidglggpedccmhohmemehpghgidaj) & follow the steps to install extension (Note: Versatus wallet is still in beta mode, so expect some issue & bugs & feel free to report it to devs on discord)

## Setup & Deploy A Program

  - Make sure you have Node.Js V18 installed in your Ubuntu. If Node.Js is not installed in your machine, you may install it using the command below:

 ```sh
sudo apt update && sudo apt install -y curl && curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - && sudo apt install -y nodejs
```
  
  -  You can verify that Node.js and npm were installed correctly by checking their versions:

```sh
node -v
```
  
  ```sh
npm -v
```
  
  - if it is showing above 18, you can skip to next step & if not, you need to upgrade your node.js using the below command  
    ```sh
    sudo apt-get remove -y nodejs
    curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
    sudo apt-get install -y nodejs
    ```
  
  - To setup your project you can use the below command. you can edit 'your-project-name' from below.

```sh
mkdir your-project-name
cd your-project-name
npm init -y
npm install typescript --save-dev
npx tsc --init
```
- Install Versatus project

```sh
npm install --save @versatus/versatus-javascript
```
- Start the project
```sh
npx lasrctl init hello-lasr
```

Now keypair.json file has generated at /your-project-name/.lasr/wallet/keypair.json
By opening this file, you can see mnemonics, secret key... copy everything & save it securely. Open it by running, you must run this command from inside of your project directory:

```sh
nano .lasr/wallet/keypair.json
```


- Now import this mnemonic / secret key to Versatus wallet & copy your wallet address.
- Go to [Discord](https://discord.com/channels/1034112774789414963/1228424731955433493) & request some test tokens from the bot.Once test tokens arrived at your wallet, do the below command
```sh
npx lasrctl build example-program.ts
```
then
```sh
npx lasrctl test -b example-program -i example-program-inputs
```
 - if You see the below response, then we are doing good until here
    ![image](https://github.com/johnwick42in/versatus/assets/74258783/2c6d44d1-18e4-40b9-a321-362fd00d4b94)

   Now deploy
   ```sh
   npx lasrctl deploy --build example-program --symbol ELON_SHITS --programName ZKscem
   ```
   Now you'll see a link to your playground. save them for later use.

## Steps to create a mintable fungible token & create a faucet

- Use the below command for setup
```sh
cd
mkdir fungible-project
cd fungible-project
npm init -y
npm install typescript --save-dev
npx tsc --init
npm install --save @versatus/versatus-javascript
npx lasrctl init fungible
```
- Now a keypair file is generated in the directory /fungible-project/.lasr/wallet/keypairs.json
- Copy & store the keys in a secure place. copy address and get some verse from discord faucet.
```sh
npx lasrctl build example-program.ts
npx lasrctl test -b example-program -i example-program-inputs
```
- Now replace YOUR_ACCOUNT_ADDRESS with your wallet address from /fungible-project/.lasr/wallet/keypairs.json & run the command. you can edit 'SYMBOL_NAME' 'PROGRAM_NAME' and supply if you want.
  
  ```sh
  npx lasrctl deploy --build example-program --symbol eigenL --programName sreeramK --initializedSupply 6900000 --totalSupply 6900000 --recipientAddress YOUR_ACCOUNT_ADDRESS \
  --txInputs '{"imgUrl":"https://pbs.twimg.com/media/F8z1khNWAAAE7WM?format=jpg&name=900x900","paymentProgramAddress": "0x9f85fb953179fb2418faf4e5560c1ac3717e8c0f","conversionRate":"1"}'
  ```
 if it deployed successfully, you will get a link to the mint page.This is your fungible program . copy & share it in their [discord server](https://discord.com/channels/1034112774789414963/1034117763532337232). Devs will take a look at it, mint it & share feedback.

 Now we have created a mintable token, we will now move on to create a faucet

```sh
npx lasrctl init faucet
npx lasrctl test -b example-program -i example-program-inputs
```
Then
 ```sh
npx lasrctl deploy --build example-program --symbol FAUCET --programName "Faucet for anything fungible" --txInputs '{"imgUrl":"https://pbs.twimg.com/profile_images/1421740863139446787/huoxhEV3_400x400.jpg"}'
```
Now you'll get a playground link. click copy & paste it in your browser. This is your faucet program.

Then
Replace 'FAUCET_PROGRAM_ADDRESS' with your Faucet program address & replace 'FUNGIBLE_PROGRAM_ADDRESS' with the your fungible program address.

```sh
npx lasrctl call --programAddress FAUCET_PROGRAM_ADDRESS --op addProgram \
  --txInputs '{"programAddress":"FUNGIBLE_PROGRAM_ADDRESS","amountToAdd":"1000","faucetAmount":"1","addressTimeoutMinutes":"1"}'
```

Finally, like previous step, change faucet and program address and replace 'SOME_OTHER_ADDRESS' with your own address from keypair.

```sh
npx lasrctl call --programAddress FAUCET_PROGRAM_ADDRESS --op faucet \
  --txInputs '{"programToSend":"FUNGIBLE_PROGRAM_ADDRESS","to":"SOME_OTHER_ADDRESS"}'
```


## ## Steps to create a non-fungible token
- We do the setup first
  
 ```sh
cd
mkdir NFT
cd NFT
npm init -y
npm install typescript --save-dev
npx tsc --init
npm install --save @versatus/versatus-javascript
```
- Then
- 
```sh
npx lasrctl init non-fungible
```

- Now a keypair file is generated in the directory /NFT/.lasr/wallet/keypairs.json
- Copy & store the keys in a secure place. copy address and get some verse from discord faucet.
- Run the below command
```sh
npx lasrctl build example-program.ts
npx lasrctl test -b example-program -i example-program-inputs
```
Now run DEPPPLOYYY using the below command. Replace YOUR_WALLET_ADDRESS with wallet address from /NFT/.lasr/wallet/keypairs.json 

```sh
npx lasrctl deploy --build example-program --programName "<PROGRAM_NAME>" --symbol <SYMBOL_NAME> --initializedSupply 4 --totalSupply 4 --txInputs '{"imgUrl":"https://i.seadn.io/gcs/files/32d179f19a42ceed7b4727b70d3352bb.jpg?auto=format&dpr=1&w=3840","price":"1","paymentProgramAddress":"YOUR_WALLET_ADDRESS","imgUrls":["https://i.seadn.io/gcs/files/5c10e1bf3028476390a65d6726f5340e.jpg?auto=format&dpr=1&w=3840","https://i.seadn.io/s/raw/files/cafd1614da6255ee880254ce349ce866.png?auto=format&dpr=1&w=3840","https://i.seadn.io/gcs/files/6850a6abc69d80c905951316ceb5949b.jpg?auto=format&dpr=1&w=3840","https://i.seadn.io/s/raw/files/94df22c9da16faaf95494f745bcc3e85.png?auto=format&dpr=1&w=3840"],"collection":"batz"}'
```
## Lets do tha faucet task now

Thanks for doing it. If you liked it please follow me on socials  [X](https://x.com/@bigiley) | [Telegram](https://t.me/johnw1k) | [Farcaster](https://warpcast.com/johnwick69)
