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
- Edit only your token in the config.yml file over [here](/config.yml#L1).
- Create a new heroku app.
- Go to the 'Deploy' tab and click 'Connect to GitHub'.
- Click on 'search' and then select your fork of this repository.
- Then 'Enable Automatic Deploys' and then select the 'master' branch (which is already done by default) and Click 'Deploy'.
- Once it has been deployed, go to 'Resources' tab on heroku and enable 'worker' (bash startbot.sh) dynos. (do note that if you don't see any dynos in the 'Resources' tab, then you must wait for about 5 minutes and then refresh your heroku page.)
- You're now connected to lishogi and awaiting challenges! Your bot is up and ready!

### Important Notes

- This code might result in many crashes, so if any error shows up in the logs, immediately restart all dynos by clucking on 'more' in the top right corner of your heroku app and then click 'restart all dynos'.
- Do note that on heroku you are allowed a maximum of 550 hours a month, so you can't run your bot 24/7 unless you have a verified account. To get a verified account you will need to provide your payment details, but no payment is required. Once this is done, your account becomes verified and you are provided an additional 450 hours a month which sums up to a total of 1000 hours a month which is more than what is needed to run your bot 24/7 on lishogi.
- This bot uses 256 MB hash size with 5 threads (heroku-20). This is quite strong, but the downside is games at a time. Heroku's free dyno's limitations are crossed even with 2-3 games in one go. So make sure you don't play many games in one go. If you want multiple games at a time, reduce the values of threads and hash in the [config.yml file](/config.yml#L14-L15) and use multithreading to handle multiple games. This is mainly caused due to rate limiting from heroku. This can be prevented by decreasing the hash and threads in the config.yml file.
- Compared to other bots, this bot plays relatively slow, and the time taken is static. We are trying to figure out a way to have better time management.
