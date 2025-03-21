# LMMS-MCP - LMMS Model Context Protocol Integration

LMMS-MCP connects LMMS to Claude AI through the Model Context Protocol (MCP), allowing Claude to directly interact with and control LMMS. This integration enables prompt-assisted music production, track creation, and session manipulation in LMMS.

## Features

* Two-way communication: Connect Claude AI to LMMS through a socket-based server
* Track manipulation: Create, modify, and manipulate tracks
* Instrument and effect selection: Claude can access and load instruments and effects
* Pattern creation: Create and edit patterns with notes
* Session control: Control playback and project parameters

## Components

The system consists of two main components:

1. LMMS Plugin/Extension: A Python-based extension for LMMS that exposes an API for controlling LMMS
2. MCP Server: A Python server that implements the Model Context Protocol and connects to the LMMS extension

## Installation

### Prerequisites

* LMMS (Latest version recommended)
* Python 3.8 or newer
* uv package manager

If you're on Mac, please install uv as:

```
brew install uv
```

Otherwise, install from [uv's official website](https://docs.astral.sh/uv/getting-started/installation/)

⚠️ Do not proceed before installing UV

### Setup Instructions

1. Install the LMMS-MCP package:

```
uv install lmms-mcp
```

2. Install the LMMS extension (see detailed instructions below)

3. Configure Claude Desktop or Cursor for MCP integration

### Claude for Desktop Integration

1. Go to Claude > Settings > Developer > Edit Config > claude_desktop_config.json to include the following:

```json
{ "mcpServers": { "LMMSMCP": { "command": "uvx", "args": [ "lmms-mcp" ] } } }
```

### Cursor Integration

Run lmms-mcp without installing it permanently through uvx. Go to Cursor Settings > MCP and paste this as a command:

```
uvx lmms-mcp
```

⚠️ Only run one instance of the MCP server (either on Cursor or Claude Desktop), not both

## LMMS Extension Installation

*Detailed instructions will be provided based on the extension development approach*

## Usage

### Starting the Connection

1. Ensure the LMMS extension is loaded in LMMS
2. Make sure the MCP server is configured in Claude Desktop or Cursor
3. The connection should be established automatically when you interact with Claude

### Using with Claude

Once the configuration is set and the extension is running in LMMS, you can use Claude to control LMMS through natural language commands.

## Capabilities

* Get project information
* Create and modify tracks
* Create and edit patterns
* Control playback
* Load instruments and effects
* Add notes to patterns
* Change tempo and other project parameters

## Example Commands

Here are some examples of what you can ask Claude to do:

* "Create a synthwave track in LMMS"
* "Create a new track with a synth bass instrument"
* "Add reverb to my drums"
* "Create a 4-bar pattern with a simple melody"
* "Get information about the current LMMS project"
* "Add a jazz chord progression to the pattern in track 1"
* "Set the tempo to 120 BPM"
* "Play the current project"

## Limitations

Unlike Ableton Live, LMMS has some limitations:

* No direct audio recording capabilities in LMMS itself
* Some advanced features available in Ableton may not be available
* The extension interfaces with LMMS through its available API or automation capabilities

## Technical Details

### Communication Protocol

The system uses a simple JSON-based protocol over TCP sockets:

* Commands are sent as JSON objects with a type and optional params
* Responses are JSON objects with a status and result or message

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Disclaimer

This is a third-party integration and not made by LMMS.
