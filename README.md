tgsay
=====
**tgsay** sends messages to Telegram via CLI. It may be used in shell scripts, cron commands, monitoring systems etc.

Requirements
------------
* *nix
* PHP 7.2

Installation
------------
1. Copy `tgsay` inside your `$PATH`.
2. If you don't have a Telegram bot yet be sure to [create one](https://core.telegram.org/bots#3-how-do-i-create-a-bot).
3. Create config (default path is `~/.config/tgsay.ini` or `/etc/tgsay.ini`):
   ```ini
   [bots]
   ; keys are bot aliases, not the actual bot names, must have at least one
   JenkinsBot   = <bot token>
   ZabbixBot    = <bot token>
    
   [chats]
   ; same here: keys are just aliases, must have at least one
   Myself       = <person id>
   TeamChat     = <chat id>
   AlertChannel = <channel id>
    
   [defaults]
   ; defaults will be used if corresponding arguments are skipped, optional
   bot          = <bot alias>
   chat         = <chat alias>

   ```

Usage
-----

Send message using specific bot and chat:
```bash
tgsay --bot="JenkinsBot" --chat="TeamChat" --msg="Build completed"
```
Send message using defaults:
```bash
tgsay --msg="Everything is fine"
```
Send silent message:
```bash
tgsay --msg="This one isn't really urgent" --slient
```
Send preformatted message:
```bash
tgsay --msg="But this one *urgent* a lot" --md
```
Use STDIN to pass message body:
```bash
cat build_log | tgsay
```
Please refer to built-in help to get more information on available options.