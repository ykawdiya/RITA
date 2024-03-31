## RITA (Stable) [![invite](https://img.shields.io/badge/Discord_Support-JOIN-7289DA.svg?)](https://discordapp.com/invite/mgNR64R)
A Translation bot built using `discord.js` and a custom `Google Translate API`.
*(The NPM Version of Google Translate API is outdated and does not work with this distribution, as such a custom and maintained version is installed.)*

### --RITA-- Master Branch
![GitHub package.json version](https://img.shields.io/github/package-json/v/ykawdiya/RitaBot?label=Stable%20Version)
[![codebeat badge](https://codebeat.co/badges/125a5ce4-4ba1-45cf-95fa-266e1353c331)](https://codebeat.co/projects/github-com-ykawdiya-ritabot-master)
[![Build Status](https://travis-ci.com/ykawdiya/RitaBot.svg?branch=master)](https://travis-ci.com/ykawdiya/RitaBot)
[![CircleCI](https://circleci.com/gh/ykawdiya/RitaBot.svg?style=svg)](https://circleci.com/gh/ykawdiya/RitaBot)
![GitHub last commit](https://img.shields.io/github/last-commit/ykawdiya/RitaBot.svg)
![GitHub](https://img.shields.io/github/license/ykawdiya/RitaBot.svg)
![GitHub issues](https://img.shields.io/github/issues/ykawdiya/RitaBot)

### --Google Translate API-- Master Branch
![GitHub package.json version](https://img.shields.io/github/package-json/v/ykawdiya/google-translate-api)
[![Build Status](https://travis-ci.com/ykawdiya/google-translate-api.svg?branch=master)](https://travis-ci.com/ykawdiya/google-translate-api)
![GitHub last commit](https://img.shields.io/github/last-commit/ykawdiya/google-translate-api)
![GitHub issues](https://img.shields.io/github/issues/ykawdiya/google-translate-api)

#### --RITA-- Current Test Branch
![GitHub package.json version (branch)](https://img.shields.io/github/package-json/v/ykawdiya/RitaBot/test-branch?label=Test%20Version)
[![Build Status](https://travis-ci.com/ykawdiya/RitaBot.svg?branch=test-branch)](https://travis-ci.com/ykawdiya/RitaBot)
[![CircleCI](https://circleci.com/gh/ykawdiya/RitaBot/tree/test-branch.svg?style=svg)](https://circleci.com/gh/ykawdiya/RitaBot/tree/test-branch)

#### --Google Translate API-- Current Test Branch
![GitHub package.json version (branch)](https://img.shields.io/github/package-json/v/ykawdiya/google-translate-api/test-branch)
[![Build Status](https://travis-ci.com/ykawdiya/google-translate-api.svg?branch=test-branch)](https://travis-ci.com/ykawdiya/google-translate-api)

## Coming Soon!

01. Error Message Support Section.
02. Auto Reverse translation for the auto function.
03. `!t tasks #TargetChannel` Implementation.
04. Introduction of a Streamlined Command Handler. (This will be done as a New Project)
05. Accept "auto" as a language for Automatic detection and translation.

## Features in 1.0.0
* Core translation functionality
* Discord integration with command support
* Multi-language support
* Embed messages option
* Automatic translation features
* Channel translation capability
* Reaction-based translation

## Table of Contents

01. [Features](#features)
02. [Usage](#usage)
03. [Setting up a New Bot (RECOMMENDED)](#new-bot)
04. [How to Update](#update)
05. [Heroku Database Support](#database)
06. [Local Installation Support](#local)
07. [Setup on a Raspberry Pi](#pi)
08. [Troubleshooting](#troubleshooting)
09. [Error Messages](#errors)
10. [Commands](#commands)
11. [Credits & License](#credits-&-license)
12. [Design Team](#design-team)
13. [What, Who, How and Why?](#history)

## <a name="features"></a>Features
* Translate custom messages
* Translate messages by reacting with flag emoji
* Translate last message(s) in channel
* Translate to multiple languages at once
* Automatic translation of channels with option to forward translations to users or separate channels.
* Supports 100+ languages

## <a name=""></a>Usage
* Create your own with the instructions below.
* Write `!translate help` or `!t help` for a list of commands.


**If you are looking to set up a New Bot then follow the instruction below.**


## <a name="new-bot"></a>Setting up a New Bot (RECOMMENDED)

**To deploy a free translation bot that you can add to your discord server, follow these easy steps.**


#### 1. Access the Rita repository.
* If you don't yet have a Github account, [create one](https://github.com/join)! It's free and easy.
* Visit the [Rita repository](https://github.com/ykawdiya/RitaBot) on GitHub.

#### 2. Create a new [Discord App](https://discordapp.com/developers/applications/me/create)
* Give app a friendly name and click the **Create App** button
  * I like the name **Rita**, but feel free to pick something different if you prefer.
* Take note of the app **CLIENT ID**, you will need it later
* Scroll down to the **Bot** section
* Click the **Create a Bot User** button
* Click the **Yes, do it!** button
* Copy the bot's **TOKEN**, you will need it later

#### 3. Create a [Heroku account](https://id.heroku.com/signup/login) (It's free!)
* Create a new app. It's name must be unique and composed of all lowercase letters and dashes. Something like `yourname-discordbot` is fine
* Under **Deployment Method** select **GitHub** and connect to your GitHub account.
* Search for the Rita repository and connect to it.
* Scroll down to the "Manual Deploy" section, select the **master** branch and click "Deploy Branch".
* Go to the **Resources** tab and look for the addons section. Search 'Postgres', and add a 'Hobby Dev - Free' version of Heroku Postgres. This will be automatically attached as your bot's database.
* Go to the **Settings** tab. Click to reveal Config Variables, then add then add the following:
  * **KEY:** =  DISCORD_TOKEN
  * **Value:** = Your discord bot's token that you copied earlier.
  * **KEY:** =  NODE_MODULES_CACHE
  * **Value:** = false
    * *This is to ensure that when the bot updates it does not use any old Dependencies that Heroku has stored and gets fresh ones from the package.json file*
* Go to the **Overview** tab and click configure dynos. Turn off the default `web npm start` dyno and turn on the `worker node src/bot.js` dyno. Your bot will now be up and running!

#### 4. Invite your bot to your server and configure it!
* Replace the CLIENTID string in the following URL with your own apps client id: https://discordapp.com/oauth2/authorize?&client_id=CLIENTID&scope=bot&permissions=8
* Visit the resulting URL and add your bot to any server where you have admin privileges.
* Once added, your bot should show up more or less instantaneously. Type `!t help` within the discord chat for more details on how to use it. Happy translating!


## <a name="update"></a>How to Update to the Latest Version
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

## <a name="local"></a>Local Installation Support
The bot can also be run locally without Heroku. The local setup requires more steps since the database needs to be setup and the development tools need be installed. 

#### 1. Create a local database
Any Database that runs with SQL Sequelize ('https://sequelize.org/master/') can be used. My recommendation is to use the [SQL Lite](https://www.sqlite.org/index.html) database since the setup is fast and access is easy. Copy the connection details to the database for the next step. Example: The connection to a sqlite database with the name *database.db* stored at the same level of this README file would be *./database.db*.

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

## <a name="supporters"></a> :clap: Supporters

[![Stargazers repo roster for @ykawdiya/RitaBot](https://reporoster.com/stars/ykawdiya/RitaBot)](https://github.com/ykawdiya/RitaBot/stargazers)
[![Forkers repo roster for @ykawdiya/RitaBot](https://reporoster.com/forks/ykawdiya/RitaBot)](https://github.com/ykawdiya/RitaBot/network/members)

------


## <a name="credits-&-license"></a>:star_struck: Credits & License

This project is developed and maintained by Yash Kawdiya. The project is released under the MIT license and is completely free to use.

------

## <a name="design-team"></a>:sunglasses: Design Team
* Yash Kawdiya / [ykawdiya](https://github.com/ykawdiya)

------

## <a name="history"></a>:yum: What is Rita?

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