# MPD Discord RPC

Displays your currently playing song / album / artist from MPD in Discord using Rich Presence. It includes support for multiple MPD hosts if, like me, you have more than one server you alternate between.

The program does not require MPD or Discord to be running in order to run.

Once installed just run `mpd-discord-rpc`.

![status](https://cdn.xndr.tech/u/6xTbjgl.png)

## Installation

Clone the repo and run `cargo build --release`

## Configuration

Running the program once will generate a default configuration file. On Linux this will be at `~/.config/discord-rpc/config.toml`

- **id** - The Discord application ID to run through. 
- **hosts** - An array of MPD server host socket addresses. 
    Each one will be tried in order until a playing server is found.
- **format** - Format strings. Tokens are listed below.
    - **details** - A format string for the top line. 
        This is the song title by default.
    - **state** - A format string for the second line. 
        This is the artist / album by default.
    - **timestamp** - The timestamp mode for the third line. 
        This is 'elapsed' by default.
        Can be one of `elapsed`, `left` or `off`. Falls back to `elapsed`.

### Formatting Tokens

Any part of the format string that does not match one of these tokens will be displayed as is.
The following will automatically be replaced with their value from MPD:

- `$title`
- `$album`
- `$artist`
- `$date`
- `$track`
- `$disc`
- `$genre`
- `$duration`
- `$elapsed`
