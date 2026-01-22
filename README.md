# Kaset Raycast Extension

Control [Kaset](https://github.com/sozercan/kaset) - YouTube Music client for macOS - directly from Raycast.

## Features

- **Now Playing** - View current track with artwork, progress, and controls
- **Toggle Play/Pause** - Quick playback control
- **Next/Previous Track** - Skip tracks
- **Volume Control** - Set volume from 0-100%
- **Toggle Shuffle** - Enable/disable shuffle mode
- **Cycle Repeat** - Cycle through repeat modes (off → all → one)
- **Toggle Mute** - Mute/unmute audio

## Requirements

- [Kaset](https://github.com/sozercan/kaset) must be installed and built with AppleScript support
- macOS 26.0 or later

## Installation

### 1. Build Kaset with AppleScript Support

Before using this extension, you need to build Kaset with the AppleScript support files that were added to the project:

1. Open `Kaset.xcodeproj` in Xcode
2. Build the project (⌘B)
3. Run Kaset at least once

### 2. Install the Extension

```bash
cd raycast-extension
npm install
npm run dev
```

This will open Raycast and load the extension in development mode.

### 3. Add Extension Icon

Replace `assets/extension-icon.png` with a 512x512 PNG icon for the extension.

## Commands

| Command | Description | Shortcut |
|---------|-------------|----------|
| Now Playing | View current track | - |
| Toggle Play/Pause | Play or pause | - |
| Next Track | Skip to next | - |
| Previous Track | Go back | - |
| Set Volume | Choose volume level | - |
| Toggle Shuffle | Toggle shuffle mode | - |
| Cycle Repeat | Cycle repeat modes | - |
| Toggle Mute | Mute/unmute | - |

## AppleScript Support

This extension communicates with Kaset via AppleScript. The following commands are available:

```applescript
-- Playback control
tell application "Kaset" to play
tell application "Kaset" to pause
tell application "Kaset" to playpause
tell application "Kaset" to next track
tell application "Kaset" to previous track

-- Volume
tell application "Kaset" to set volume 50
tell application "Kaset" to get sound volume

-- Modes
tell application "Kaset" to toggle shuffle
tell application "Kaset" to cycle repeat
tell application "Kaset" to toggle mute

-- State
tell application "Kaset" to get player state
tell application "Kaset" to get shuffling
tell application "Kaset" to get repeating
tell application "Kaset" to get muted

-- Current track
tell application "Kaset"
  set t to current track
  name of t        -- track title
  artist of t      -- artist name
  album of t       -- album name
  duration of t    -- duration in seconds
  id of t          -- video ID
  artwork url of t -- artwork URL
end tell

-- Position
tell application "Kaset" to get player position
tell application "Kaset" to set player position to 30
tell application "Kaset" to get track duration
```

## Development

```bash
# Install dependencies
npm install

# Run in development mode
npm run dev

# Build for production
npm run build

# Lint
npm run lint
npm run fix-lint
```

## License

MIT
