A Step by Step guide to Deploy A Program & create Fungible & Non-Fungible tokens on Versatus backed by Jump, Big Brain Holdings, NGC Ventures & more...

Projects Official links  
   Website : http://versatus.io/
   Twitter : https://twitter.com/VersatusLabs
   Discord : https://discord.gg/versatus

Disclaimer : This guide purely intends for educational purpose.

I. Steps for Downloading Versatus Wallet Extension.(Note: Versatus wallet is still in beta mode, so expect some issue & bugs & feel free to report it to devs on discord)

   1. Go to https://itero.plasmo.com/ext/omkbidglggpedccmhohmemehpghgidaj & follow the steps to install extension.

II. Setup & Deploy A Program

   1. Make sure you have Node.Js V18 installed in your Ubuntu. To check node.js version run the below code
            node -v
   2. if it is showing above 18, you can skip to next step & if not Version 18, you need to upgrade your node.js using the below command  
            sudo apt-get remove -y nodejs
            curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
      		sudo apt-get install -y nodejs
	3. To setup your project you can use the below command
      		mkdir your-project-name
				cd your-project-name
				npm init -y
				npm install typescript --save-dev
				npx tsc --init
	4. Install Versatus project
				npm install --save @versatus/versatus-javascript
	5. 
      
