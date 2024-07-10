# Twitch Chat Plays Bot
[![Stand With Ukraine](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/badges/StandWithUkraine.svg)](https://stand-with-ukraine.pp.ua)


A Python script for Twitch Chat interaction with almost any game.
###### I have only tested this on Windows.

----
### Prerequisites:
- Python https://www.python.org/downloads/ (tested with 3.10)
- Download Autohotkey from https://www.autohotkey.com/ and provide the .exe path to line 5 of the script. 
- Install ahk through pip - https://pypi.org/project/ahk/
- Get your Twitch oauth key from https://twitchapps.com/tmi/ (DO NOT SHARE THIS!), and paste the key on line 10 between the parentheses. 

----
### The Setup:

#### Line 5 - Replace 'PATH' with AHK .exe path location.
###### Example: 'C:\Program Files\AutoHotkey\AutoHotKey.exe'
```python
    ahk = AHK(executable_path='PATH')
```

#### Line 10 - Add the oauth code that was generated from https://twitchapps.com/tmi/ here (include "oauth:" that is apart of the generated code).
###### DO NOT SHARE THIS KEY!
```python
    PASS = "OAUTH_CODE"
```

#### Line 11 - Name the bot
```python
    BOT = "BOT_NAME"
```

#### Line 12 - Add the name of the Twitch channel you want to monitor.
```python
    CHANNEL = "CHANNEL_NAME"
```

#### Line 13 - Add your Twitch account name.
```python
    OWNER = "ACCOUNT_NAME"
```

----
### Tweaking:

#### Game controls are handled by condition checks(if chat sends "up", AHK will read "up" and pass the command to the game).
###### You may need to go into game settings to reconfigure keymap for each game.
###### See below example(s):
```python
    # For an "UP" Press:
    if "up" == message.lower():
        ahk.key_press('up')
        message = ""
```
###### alternatively, add and remove conditions as you seem fit.
```python
    # For a "DOWN" Press:
    if "down" == message.lower():
        ahk.key_press('down')
        message = ""
```

----
### Run the Script:
#### Navigate to the project directory using CMD or Terminal and run the command:
```shell
    py twitchchatplays.py
```

###### Successful output example:
```shell
    :tmi.twitch.tv 001 :Welcome, GLHF!
    :tmi.twitch.tv 002 :Your host is tmi.twitch.tv
    :tmi.twitch.tv 003 :This server is rather new
    :tmi.twitch.tv 004 :-
    :tmi.twitch.tv 005 :-
    :tmi.twitch.tv 006 :You are in a maze of twisty passages, all alike.
    :tmi.twitch.tv 007 :>
    
    :tmi.twitch.tv 001 :Welcome, GLHF!
    :tmi.twitch.tv 002 :Your host is tmi.twitch.tv
    :tmi.twitch.tv 003 :This server is rather new
    :tmi.twitch.tv 004 :-
    :tmi.twitch.tv 005 :-
    :tmi.twitch.tv 006 :You are in a maze of twisty passages, all alike.
    :tmi.twitch.tv 007 :>
    :name!name@name.tmi.twitch.tv JOIN #name
    :name.tmi.twitch.tv 008 name = #name :name
    :name.tmi.twitch.tv 009 name #name :End of /NAMES list
    
    :name!name@name.tmi.twitch.tv JOIN #name
    :name.tmi.twitch.tv 001 name = #name :name
    :name.tmi.twitch.tv 002 name #name :End of /NAMES list
    BOT has joined name's Channel!
    tmi.twitch.tv CAP * ACK  : twitch.tv/tags
    -- Twitch chat messages will show up here. --
```

###### * Testing will be unresponsive from host machine running the script.
###### You will need to test from another device, or get a friend to login to Twitch and test inputs that way.
