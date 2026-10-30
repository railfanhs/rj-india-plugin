# RailJournal for Claude

Look up Indian Railways trains and stations from [RailJournal](https://railjournal.in) inside Claude.

## What it does

The plugin connects Claude to the RailJournal MCP server, a read-only service with seven tools:

| Tool | Purpose |
| --- | --- |
| `search_trains` | Find a train by name or partial number |
| `get_train_info` | Train profile, operating days, classes and timetable |
| `search_stations` | Find a station by name or code |
| `get_station_info` | Station name, location, zone, division and facts |
| `find_trains_between_stations` | Trains running from one station to another, with times and operating days |
| `server_status` | Health check: server version and available tools |
| `get_train_running_status` | Live running status from the RailJournal NTES feed |

It also ships three skills that tell Claude how to use the tools well: `find-train-or-station`, `train-status` and `journey-check`.

## Example prompts

- "What is train 12951 and which days does it run?"
- "Find the station code for Mumbai Central and tell me about it."
- "How is 12301 running today?"
- "Does 12951 go from Mumbai Central to New Delhi, and how long does it take?"

## Data and privacy

All data comes from RailJournal's own database and caches. No account or login is needed, and the plugin does not read or write personal data. The plugin only asks for train numbers, station names or codes and dates. See the [privacy policy](https://railjournal.in/AI_plugins/Claude/privacy.html).

## Limits

Running status is read from a cache and can be unavailable. Timetable platforms are scheduled, not live. The service is rate limited, so Claude sends calls one at a time. The plugin does not book tickets or check seat availability.

## Support

Contact railjournalindia@gmail.com.

## License

MIT
