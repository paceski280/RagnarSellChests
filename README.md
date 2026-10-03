# RagnarSellChests

RagnarSellChests adds timed automatic SellChests to Paper servers and uses EconomyShopGUI as the source of sell prices.

## Features

- Automatic selling using EconomyShopGUI prices
- Finite SellChest lifetimes (no permanent chests)
- Configurable sell interval and multipliers
- Selling pauses while the owner is offline; lifetime expiration does not
- Live TextDisplay holograms with owner, remaining time, multiplier, earnings and next sale
- Single and double chest support
- Protection against unauthorized access, breaking and explosions
- Configurable allowed worlds
- Configurable per-rank limits through permissions
- Persistent chest data
- English messages and configuration

## Requirements

- Java 21
- Paper 1.21.11
- EconomyShopGUI with a supported economy provider

## Installation

1. Install EconomyShopGUI and configure its economy provider.
2. Place `RagnarSellChests-1.3.0.jar` in your server's `plugins` folder.
3. Restart the server.
4. Edit `plugins/RagnarSellChests/config.yml` and `messages.yml` if needed.

## Commands

`/sellchest give <player> <duration> [boost]` — Gives a SellChest token.

Examples:

- `/sellchest give Steve 30d`
- `/sellchest give Steve 60d 1.25`
- `/sellchest reload`

Aliases: `/sellchests`, `/rsc`

## Permissions

- `ragnarsellchests.admin` — Administrative commands and owner bypass.
- `ragnarsellchests.limit.<rank>` — Applies the configured limit for `<rank>`.

Rank names are not hardcoded. You can define your own in `config.yml`:

```yaml
limits:
  default: 1
  vip: 2
  premium: 3
  legend: 5
```

A player with `ragnarsellchests.limit.premium` can own up to 3 SellChests. If multiple limit permissions are present, the highest configured limit is used.

## Duration behavior

The lifetime begins when the SellChest is placed. It continues in real time even when the owner is offline. Automatic sale attempts only progress while the owner is online.

## Building

Clone the repository and run:

```bash
mvn clean package
```

The compiled plugin will be created in the `target/` directory.

## License

RagnarSellChests is licensed under the MIT License. See [LICENSE](LICENSE).

## Author

paceski28
