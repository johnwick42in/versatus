# A Step by Step guide to Deploy A Program & create Fungible & Non-Fungible tokens on Versatus backed by Jump, Big Brain Holdings, NGC Ventures & more...
![img](https://pbs.twimg.com/profile_banners/1465798967657209857/1695224624/1500x500)


Projects Official links
   - Website : http://versatus.io/
   - Twitter : https://twitter.com/VersatusLabs
   - Discord : https://discord.gg/versatus

## Steps for Downloading Versatus Wallet Extension.
   - Go to [this link](https://itero.plasmo.com/ext/omkbidglggpedccmhohmemehpghgidaj) & follow the steps to install extension (Note: Versatus wallet is still in beta mode, so expect some issue & bugs & feel free to report it to devs on discord)

## Setup & Deploy A Program

  - Make sure you have Node.Js V18 installed in your Ubuntu. To check node.js version run the below code
    ```sh
    node -v
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
- Now keypair.json file has generated at /your-project-name/.lasr/wallet/keypairs.json
- by opening this file, you can see mnemonics, secret key... copy everything & save it securely.
- Now import this mnemonic / secret key to Versatus wallet & copy your public address.
- Go to [Discord](https://discord.com/channels/1034112774789414963/1228424731955433493) & request some test tokens from the bot.Once test tokens arrived at your wallet, do the below command
```sh
npx lasrctl build example-program.ts
```
then
```sh
npx lasrctl test -b example-program -i example-program-inputs
```
 - if You see the below response, then we are doing until here
    ![image](https://github.com/johnwick42in/versatus/assets/74258783/2c6d44d1-18e4-40b9-a321-362fd00d4b94)

   Now deploy
   ```sh
   npx lasrctl deploy --build example-program --symbol HELLO_WORLD --programName MY_FIRST_PROGRAM
   ```
   Now you'll see a link to your playground. save them for later use.
   

 
      
