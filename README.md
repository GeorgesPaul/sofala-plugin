# Sofala marketplace

Sell and buy on [Sofala](https://sofala.market), a general marketplace built to be used through AI assistants. Sofala has classified-style listings of goods, real estate and services, open to anyone anywhere, and digital goods (browser games, eBooks, music, video, software and design files) that are bought and delivered on the site.

With this plugin Claude can:

- write a listing from a photo and a sentence, pick the category, fill in its attributes and publish it once you approve
- search listings with filters, ask sellers questions and make offers for you
- keep track of your messages, offers, deals and saved searches
- publish a game, eBook, album or film you made, upload its files and ship new builds

## What is in the plugin

- **A connection to the Sofala MCP server** at `https://sofala.market/mcp`. This is the only service the plugin talks to. The first time Claude uses it you sign in to your Sofala account in the browser (OAuth); a new account is free and takes an email code.
- **Three skills** that teach Claude how to use it well:
  - `sell-item`: list an item, a property or a service, and handle questions and offers
  - `find-and-buy`: search, talk to sellers, make offers, buy digital goods
  - `publish-digital`: publish a browser game, eBook, music or video and send new builds

The plugin has no hooks, runs no scripts and installs no packages.

## Install

In Claude Code:

    claude plugin marketplace add GeorgesPaul/sofala-plugin
    claude plugin install sofala@sofala-market

Then ask, for example:

- "Sell this chair on Sofala" (with a photo)
- "Find a used road bike under 400 euros near Lisbon on Sofala"
- "Publish my game on Sofala: the build is in dist/game.zip"

## What Claude does and does not do

- Claude asks before anything that commits you or that other people see: publishing or changing a listing, sending a message, making or answering an offer, confirming a handover, cancelling a deal, rating.
- Sofala does not handle payment for goods, property or services: buyer and seller arrange it themselves. Digital goods are paid on Sofala through a checkout link that you open and pay yourself. Claude never pays and never asks for card details.

## Privacy

The plugin sends data only to `sofala.market`: what you ask Claude to search for, list, message or upload, under your own Sofala account. The privacy policy is at https://sofala.market/privacy and the terms are at https://sofala.market/terms.

## Support

Write to info@sofala.market.

## License

MIT. See [LICENSE](LICENSE).
