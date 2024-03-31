<p align="center"><a href="https://ritabot.org/"><img src="https://media3.giphy.com/media/YO4a0qsdVX3Gq3darL/giphy.gif" data-canonical-src="https://media3.giphy.com/media/YO4a0qsdVX3Gq3darL/giphy.gif" width="175" height="175" href="https://ritabot.org/"></a></p>
<h1 align="center">Rita</h1>
<p align="center">Breaking the language barrier for free.</p>

------

<p align="center">
<img src="https://img.shields.io/github/package-json/v/ykawdiya/RitaBot?label=Stable%20Version"> <a href="https://discordapp.com/invite/mgNR64R"><img src="https://img.shields.io/badge/Discord_Support-JOIN-7289DA.svg?"></a><a href="https://opensource.org/licenses/MIT"> <img src="https://img.shields.io/github/license/ykawdiya/RitaBot.svg"> </a> <a href="https://github.com/ykawdiya/RitaBot/tree/test-branch-1.3.0/"><img src="https://img.shields.io/github/package-json/v/ykawdiya/RitaBot/test-branch-1.3.0?label=Test%20Version"></a> <a href="https://github.com/ykawdiya/RitaBOt/stargazers/"> <img src="https://img.shields.io/github/stars/ykawdiya/RitaBot" href="https://github.com/ykawdiya/RitaBot/stargazers"> </a>
 <img src="https://img.shields.io/github/checks-status/ykawdiya/RitaBot/ed616d5df0c63cfde954b4ea36fbab13c1ad86a6?label=build"> <a href="https://github.com/ykawdiya/RitaBot/fork"> <img src="https://img.shields.io/badge/dynamic/json?color=success&label=forks&query=forks&url=https%3A%2F%2Fapi.github.com%2Frepos%2Fykawdiya%2FRitaBot"> </a>
</p><br/><br/>



<p align="center">An open-source, free Discord Translator Bot built using <strong>google-translate-api</strong> and <strong>Discord.js</strong>.</p>

![Rita Translator Diagram](https://storage.pixteller.com/designs/designs-images/2021-02-03/05/poster-simple-quote-1-601a17471d0b6.png)

##### If you like what we are doing, please [star](https://github.com/ykawdiya/RitaBot/stargazers) our repo using the top-right star icon




## :book: Table of Contents

*Please note some of these links direct you towards our website*
<details>
<summary></strong>Click to expand contents</strong></summary>

* [Setting up Rita](#new-bot)
* [Setting up Rita locally](#local)
* [How to Update your Bot](#update)
* [Coming Soon](#soon)
  * [Heroku Database Support](https://ritabot.org/dbsupport/)
  * [Setup on a Raspberry Pi](https://ritabot.org/raspberry-pi/)
  * [Whats New with Rita](https://ritabot.org/whats-new/)
  * [Features](https://ritabot.org/features)
  * [Usage](https://ritabot.org/usage/)
  * [How to Update your Database Manually](https://ritabot.org/dbsupport/)
  * [C-3PO to RITA Bot Migration](https://ritabot.org/migration/)
  * [Webhook Log Setup](https://ritabot.org/troubleshooting)
  * [Common Issues](https://ritabot.org/common-issues)
  * [Command Wiki](https://ritabot.org/wiki)
    * [Supporters](#supporters)
    * [Credits & License](#credits-&-license)
    * [Design Team](#design-team)
    * [About Us](#history)
</details>

------

## <a name="new-bot"></a>:computer: Setting up Rita Translator on Heroku

<p align="center">
<img src="https://github-images.s3.amazonaws.com/help/bootcamp/Bootcamp-Fork.png">
</p><br/><br/>

#### 1. Access the Rita repository.
* If you want to contribute, [create a GitHub account](https://github.com/join) if you don't have one.
* Visit the [Rita repository](https://github.com/ykawdiya/RitaBot) on GitHub.


* Please ***star our project*** if you like it using the top-right Star icon. Every star helps us! 
<p align="center">
<img src="https://ritabot.org/index//images/star.png" href="https://github.com/ykawdiya/RitaBot/stargazers">
</p><br/><br/>

#### 2. Create a new [Discord Application](https://discordapp.com/developers/applications) in the Discord Developer Portal
* Give app a friendly name and click the **Create App** button
  * I like the name **C-3PO**, but feel free to pick something different if you fear George Lucas's wrath. Maybe **C-4PO**
* Take note of the app **CLIENT ID**, you will need it later
* Scroll down to the **Bot** section
* Click the **Create a Bot User** button
* Click the **Yes, do it!** button
* Copy the bot's **TOKEN**, you will need it later

#### 3. Create a [Heroku account](https://id.heroku.com/signup/login) (It's free!)
* Create a new app. It's name must be unique and composed of all lowercase letters and dashes. Something like `yourname-discordbot` is fine
* Under **Deployment Method** select Github. Connect to your Github account and search for this repository by name.
* Scroll down to the manual deploy section, and select the **Master** branch. Click deploy branch, and wait for the successfully deployed message.

* Go to the **Resources** tab and look for the addons section. Search 'Postgres', and add a 'Hobby Dev - Free' version of Heroku Postgres. This will be automatically attached as your bot's database.
* Go to the **Settings** tab. Click to reveal Config Variables, then add then add the following:
  * **KEY:** =  DISCORD_TOKEN
    * **Value:** = Your discord bot's token that you copied earlier.
  * **KEY:** =  NODE_MODULES_CACHE
     * **Value:** = false
    * *This is to ensure that when the bot updates it does not use any old Dependencies that Heroku has stored and gets fresh ones from the package.json file*
* Go to the **Overview** tab and click configure dynos. Turn off the default `web npm start` dyno and turn on the `worker node src/bot.js` dyno. Your bot will now be up and running!


###### **Make sure that you have added the `Heroku Postgres` Addon in the Resources Tab of Heroku or else your bot shall not run!**

* *If you have any issues running your bot join our [Discord Server](https://discord.gg/invite/mgNR64R)*
#### 4. Invite your bot to your server and configure it!
* Replace the CLIENTID string in the following URL with your own apps client id from Step 2: 
    *  **https://discordapp.com/oauth2/authorize?&client_id=CLIENTID&scope=bot&permissions=8**
    
* Visit the resulting URL and add your bot to any server where you have admin privileges.
  * Once added, your bot should show up as online, **now go back to [Heroku](https://heroku.com/) and go to the "Deploy" section, scroll down to "Manual Deploy" and deploy the *master* branch. Once finished deploying type in `!t settings dbfix`, `!t settings updatedb` and`!t embed on` or `!t embed off` in chat and you are good to go!**
    * Your bot is now setup and ready for any translation you have for it to do. Use the commands `!t help` and `!t help modules` to learn more about the commands Rita has!
  

* **Important Note**
 * The `!t embed` command is changeable whenever you like. It simply decides wether you would like translations to be sent as Webhooks (more user-like, profile picture) or embed (bot sends message with anembed message contintaining user profile picture.)

------

## <a name="update"></a>:floppy_disk: How to Update to Stable Branch on Heroku
#### 1. Checklist
* You must have a bot already running on your server, if not then refer to [Setting up a New Bot](#new-bot)

#### 2. Update to the latest version
* Download the latest version from the [releases page](https://github.com/ykawdiya/RitaBot/releases).


#### 3. Deploy Updated Version in Heroku
* Log in to your Heroku account.
* Select the bot you made in Step 3 of [Setting up a New Bot](#new-bot)
* Under **Deployment Method** select **GitHub** and connect to your GitHub account.
* Search for the Rita repository and connect to it.
* Scroll down to the "Manual Deploy" section, select the **master** branch and click "Deploy Branch".
* Wait for the "Successfully deployed" message.

#### 4. Updating Database

* Once the bot has been deployed, you will need to update the database using some commands.
* Run the following commands in order
  * **`!t settings updatedb`**
  * **`!t settings dbfix`**
  * **`!t embed on`** or **`!t embed off`** (value of the translation style)
------

## <a name="local"></a>:desktop_computer: Running Rita Locally

*The bot can also be run locally on a device. The local setup requires more steps since the database needs to be setup and the development tools need be installed. Please note that for the bot to continue running 24/7, the process of `node src/bot.js` should always remain online and thus your PC/hosting device must remain online too*

#### 1. Create a local database
Any Database that runs with [SQL Sequelize](https://sequelize.org/master/) can be used. My recommendation is to use the [SQL Lite](https://www.sqlite.org/index.html) database since the setup is fast and access is easy. Copy the connection details to the database for the next step. Example: The connection to a sqlite database with the name *`database.db`* stored at the same level of this README file would be *`./database.db`*.

#### 2. Install necessary software
Install [node.js](https://nodejs.org/en/) and make sure you have [Git](https://git-scm.com/downloads) and [npm](https://www.npmjs.com/get-npm) installed

#### 4. Install the bot
* Run **```git clone https://github.com/ykawdiya/RitaBot```**
* Download dependencies using **`npm install`**

#### 5. Create a new .env File
Rename the existing **.env.example** file and name it **.env**. Edit the Values of **DISCORD_TOKEN**, and the **DATABASE_URL** according to the values that you in [Step 2 of "Setting Up a New Bot"](#new-bot) .
  * DATABASE_URL needs to be the path to the database file (if you set **`DATABASE_URL`** to any of these values: `./database.db`, `C:/FOLDER/ok.db`, `../random.db` they will all work because they lead to a directory in which SQLite then creates the `.db` file )
    * Example -  `DATABASE_URL` = `C:\Admin\Rita_Development\test.db`

#### 5. Invite your bot to your server and configure it!
* Replace the **CLIENTID** string in the following URL with your own apps client id: https://discordapp.com/oauth2/authorize?&client_id=**CLIENTID**&scope=bot&permissions=8
  * Visit the resulting URL and add your bot to any server where you have admin privileges.

* Once added, your bot should show up as online. However, the first deploy is always broken so you have to turn it off and deploy the bot again.
  * When you first run it ***restart/deploy the bot once(again)*** and then type in chat the following commands:
    * `!t settings dbfix`
    * `!t settings updatedb`
    * `!t embed on` or `!t embed off`
  * Your bot is now setup and ready for any translation you have for it to do. Use the commands `!t help` and `!t help modules` to learn more about the commands Rita has!

------
### <a name="soon"></a>:bulb: Coming Soon!

01. Error Message Support Section.
02. Auto Reverse translation for the auto function.
03. `!t tasks #TargetChannel` Implementation.
04. Introduction of a Streamlined Command Handler. (This will be done as a New Project)
05. Update to Discord.js V12 (V1.3.0)
06. Allow Bot Translation (V1.3.0)
07. Webhooks (`!t embed off` version) using Nickname instead of Username (1.3.0) 
08. Check what language translation requests are orignally in to stop unnecessary translations and to make automatic-same channel translation ethical (1.3.0)
09. Discord slash commands introduction

------

### <a name="supporters"></a> :clap: Supporters

[![Stargazers repo roster for @ykawdiya/RitaBot](https://reporoster.com/stars/ykawdiya/RitaBot)](https://github.com/ykawdiya/RitaBot/stargazers)
[![Forkers repo roster for @ykawdiya/RitaBot](https://reporoster.com/forks/ykawdiya/RitaBot)](https://github.com/ykawdiya/RitaBot/network/members)

------


### <a name="credits-&-license"></a>:star_struck: Credits & License

This project is developed and maintained by Yash Kawdiya. The project is released under the MIT license and is completely free to use.

------

### <a name="design-team"></a>:sunglasses: Design Team
* Yash Kawdiya / [ykawdiya](https://github.com/ykawdiya)

------

### <a name="history"></a>:yum: What is Rita?

*Rita is a Real-Time Translator Bot for use on Discord, Hosted using Heroku and Local Devices and Completely **100%** Free. Rita stands for Real-Time Interchangeable Translating Assistant and helps break the language barrier on Discord servers.*

------

#### :world_map: Why was Rita created?

*Rita was created to solve the language barrier problem on Discord servers. When people from different countries and language backgrounds come together, communication can be difficult. Rita translates messages in real-time, allowing everyone to understand each other regardless of their native language.*

------

#### :star2: What makes Rita special?

*Rita offers seamless translation capabilities within Discord, supporting multiple languages and various translation modes. The bot is designed to be user-friendly, reliable, and completely free to use.*

------
###### *Rita - Breaking the language barrier for free.*



***Released under MIT license.***
