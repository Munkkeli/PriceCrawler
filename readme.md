# PriceCrawler

## How it works?

PriceCrawler will create a `db.json` with product prices, and notify the user if the price changed. User will also be notified if PriceCrawler is not able to get new price data for over a day.

## How to use?

1. Install Node.js and run `npm install`

2. Register a Telegram bot by sending a message to https://t.me/BotFather, and create a `.env` file with the bot ID, example:
  ```
  TELEGRAM_BOT_KEY = 000000000:AAAAAAA-BBBBBBBBBBBBBBBBBBBBB-CCCCC
  ```

  > More info on Telegram bots: https://core.telegram.org/bots#creating-a-new-bot

3. Run `node getTelegramChatID.js`, and press start on your new bot, the bot shoud respond with the chat ID. Add this chat ID to the end of `.env`, example:
  ```
  TELEGRAM_BOT_KEY = 000000000:AAAAAAA-BBBBBBBBBBBBBBBBBBBBB-CCCCC
  TELEGRAM_CHAT_ID = 000000000
  ```

4. Populate `watchlist.json` with the product IDs you want to monitor. More info on how to get them below. Example:
  ```
  {
    "verkkokauppa": ["2466", "31223"],
    "jimms": ["1750"]
  }
  ```

5. The bot crawls the price data every time `node index.js` or `npm start` is run. You should make one of these commands execute every 1h or so. Below is an example on how to do this with `crontab`.

  ```
  crontab -e

  Choose 1-4 [2]: *Enter*

  *Scroll to bottom*

  *Add line, this will run index.js with node every hour*
  0 * * * * node [FULL PATH TO CURRENT FOLDER]/index.js

  CTRL+X
  y
  *Enter*
  ```

## Supported stores

- Verkkokauppa.com
  - ID = /fi/product/`2466`/jtvxr/Verkkokauppa-com-jalkapallo
- Jimms.fi
  - ID = /fi/Product/Show/`1750`/jimms-kasaus/jimm-s-tietokoneen-kokoonpano-ja-testaus