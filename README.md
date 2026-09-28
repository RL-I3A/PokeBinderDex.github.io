# 📖 PokeBinderDex

Printable Pokédex, set and master set pages for Pokémon TCG collectors, plus a scanner that tells you which Pokémon are missing from your binder.

Live site: [pokebinderdex.com](https://pokebinderdex.com)

![PokeBinderDex preview](assets/blur_dex.webp)

## About

PokeBinderDex publishes print-ready A4 PDFs for organizing a Pokémon card collection. You print the pages, cut the cards along the guides and organize them in a binder. Collections are sold on Payhip and Etsy.

This repository contains the source of the website: the storefront, the Binder Scanner and the PersonalizedDex generator.

## 🃏 Collections

- **SoloDex**: all 1025 Pokémon in four styles (black silhouette, blurred, pixel, color). Available in English, French, German, Spanish and Italian.
- **SoloSet**: every card of a set (151, Shrouded Fables, Stellar Crown, Surging Spark), without variants.
- **SoloMasterSet**: the same sets, with reverse holos included.
- **FavoriMon**: every card of a given Pokémon, organized by generation.
- **FavoriIllustrator**: every card by a given illustrator.

Bundles are also available for each family.

## 🔍 Binder Scanner

Take photos of your binder pages, upload up to 50 images and pick the language of your cards (English, French, Italian, German or Spanish). The scanner returns:

- the list of detected Pokémon, with the image each one was found on
- completion stats: global, by generation, by type, legendaries and starters
- a PDF checklist of the full Pokédex with the detected Pokémon checked off
- a copy-ready list of missing Pokémon numbers, which can be pasted into PersonalizedDex

Recognition runs on a separate model hosted on Hugging Face Spaces and called from the browser through the Gradio JavaScript client. Uploaded images are sent to that service for processing.

## PersonalizedDex

A generator that builds a PDF containing only the Pokémon you choose, which saves ink and paper. You can:

- search by name or number
- paste a bulk list of Pokémon numbers
- add a whole generation in one click
- pick one of four styles: black silhouettes, outline, light outline, ultra light outline

Access is gated by a token issued after payment and validated by a small backend. PDF generation is handled by a separate API.

## Tech

The site is plain HTML, CSS and JavaScript with no build step, hosted on GitHub Pages under a custom domain. The scanner uses ES modules, [jsPDF](https://github.com/parallax/jsPDF) for the checklist and the Gradio client for recognition.

## Project structure

```
.
├── index.html                    # Storefront: collections, bundles, polls
├── scanner.html / .css / .js     # Binder Scanner
├── personalizedDex.html          # PersonalizedDex generator (token-gated)
├── PersonalizedDexPayment.html   # PersonalizedDex checkout page
├── payment-cancel.html
├── pokedex.js                    # Names (5 languages), types, generations
├── search_database.js            # Data for the FavoriMon search
├── search_functionality.js       # FavoriMon search and full list
├── votes.js                      # Poll widget
├── bandeau_script.js             # Banner script
├── modal_script.js               # Modal script
├── PokeBinderDex.css
├── assets/                       # Images, logos, videos
└── CNAME                         # Custom domain
```

## Disclaimer

Pokémon is a registered trademark. This is a fan-made project and is not affiliated with Nintendo or The Pokémon Company.

## Contact

pokebinderdex@gmail.com
