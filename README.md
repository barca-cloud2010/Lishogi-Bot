# lishogi-bot

[![Python Build](https://github.com/The-bot-makers/Lishogi-Bot/actions/workflows/python-build.yml/badge.svg)](https://github.com/The-bot-makers/Lishogi-Bot/actions/workflows/python-build.yml)

The code template to make a Lishogi Bot and deploy it to heroku server easily.

This is the code of [@TheB0t-PlAyInG-sH0gI](https://lishogi.org/@/TheB0t-PlAyInG-sH0gI) in [lishogi.org](https://lishogi.org)

Engine communication code taken from https://github.com/TheYoBots/Lishogi-Bot by [TheYoBots](https://github.com/TheYoBots)

### Shogi Engine

- Fairy Stockfish 13 POPCNT + SSE41

### Heroku Buildpack

- heroku/python

### Heroku Stack

- heroku-20 (allowing a maximum hash size of 512 mb)

### How to Use

- Fork this repository.
- Edit only your token in the config.yml file over [here](https://github.com/the-bot-makers/Lishogi-Bot/blob/master/config.yml#L1).
- Create a new heroku app.
- Go to the 'Deploy' tab and click 'Connect to GitHub'.
- Click on 'search' and then select your fork of this repository.
- Then 'Enable Automatic Deploys' and then select the 'master' branch (which is already done by default) and Click 'Deploy'.
- Once it has been deployed, go to 'Resources' tab on heroku and enable 'worker' (bash startbot.sh) dynos. (do note that if you don't see any dynos in the 'Resources' tab, then you must refresh your heroku page.)
- You're now connected to lishogi and awaiting challenges! Your bot is up and ready!

### Important Notes

- Make sure to disable/switch off the dyno once you are not monitoring your bot, for the bot used to crash in ultrabullet and bullet often. In the recent very few games, this stopped happening, but until it is fully tested, switch off the dyno when you are monitoring your bot. If any error shows up in the logs, immediately restart all dynos by more-restart all dynos.
- Also swith off your bot when you are shutting your computer down, else it might crash. This happens due to the bot losing connection with heroku. To prevent this your internet has to be running smoothly and constantly connected to heroku.
- This bot uses 256 MB hash size with 5 threads. This is quite strong, but the downside is games at a time. Heroku's free dyno's limitations are crossed even with 2-3 games in one go. So make sure you don't play many games in one go. If you want multiple games at a time, reduce the values of threads and hash in the lishogibot.py and use multithreading to handle multiple games. This is mainly caused due to rate limiting from heroku or lishogi. This can be prevented by increasing 'rate_limiting_delay' in the 'config.yml' file.
- Compared to other bots, this bot plays relatively fast, and the time taken is static. We are trying to figure out a way to have better time management.
