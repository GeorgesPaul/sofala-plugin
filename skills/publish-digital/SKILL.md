---
name: publish-digital
description: Publish a digital good on Sofala for the person who made it (a browser game, an eBook, an album, a film or course, software or design files). Use when the person wants to sell or give away something digital they made, or to ship a new build of a game that is already listed.
---

# Publish a digital good on Sofala

Digital goods (category `digital`) are paid on Sofala and delivered on the site: games are played on the page, eBooks are read, music and video are streamed, files are downloaded. Upload only what the person made or has the right to sell.

## Steps

1. Find the right subcategory with `list_categories` and read `get_category`: it says which file formats and sizes it takes and, for a browser game, how to package the ZIP.
2. Agree the title, description, price and cover image with the person.
3. Call `create_listing`. A digital listing is always saved as a draft first.
4. Call `upload_files` with the name of each file and its size in bytes. The result has an `upload_url` per file: send the file there with HTTP PUT, for example `curl -fsS -T game.zip "<upload_url>"`. A file over 64 MB goes in pieces, each PUT to `<upload_url>?offset=<bytes already sent>`. If the file is already online, pass `download_url` instead and Sofala fetches it.
5. Sofala checks each file: a game ZIP is unpacked, audio and video are prepared for streaming. Call `get_listing` until every file is `ready`. For a game it also gives a play link, so the person can try it before it goes public.
6. When the person says go, publish with `change_listing_status`.

## A new build of a game

Call `upload_files` with `replace: true` and send the new ZIP. The old build keeps running until the new one is ready, then the new one takes its place at the same address. Players keep their saves.

## Getting paid

- Paid items need payouts, which the person sets up once on the Sofala website. You cannot do that for them.
- Sellers in countries the payment provider cannot pay out to sell directly: the buyer pays them outside Sofala, and the seller gives access with `give_access` once the money has arrived.
- Licence keys and game codes are added with `update_listing` (`codes`), one per buyer.
