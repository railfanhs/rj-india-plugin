---
name: journey-check
description: Check whether an Indian train runs between two stations and show the departure, arrival, travel time, operating days and, if asked, live delay. Use when the user asks about travelling from one station to another on a named or numbered train.
---

# Journey check

Use the RailJournal tools to check a trip between two stations on a specific train. The tools cannot list every train between two stations, so this works from a train the user names or numbers.

1. Resolve both stations with `search_stations`. If a name matches several stations, show the candidates and ask the user to choose. Never guess.
2. Get the train from the user. Resolve a name with `search_trains` and confirm the match. If the user gave no train, say plainly that the tools cannot search by route and ask for a train name or number. Do not invent trains.
3. Call `get_train_info` for each train (at most three). Using the timetable, check that the train stops at both stations and that the origin comes before the destination in stop order. If it does not, say so and do not suggest it for this trip.
4. For each valid train, report the departure from the origin, the arrival at the destination, the day offset if the trip crosses midnight, the travel time and the distance between the two stops, the operating days and the travel classes. Platforms are scheduled, not live.
5. Only if the user asks how it is running today, call `get_train_running_status`. It needs the date the train left its own first station, which may differ from the date the user boards. Report the delay and last known location, and note that starred times are estimates.

Rules:
- Call tools one at a time and do not loop on failures.
- Dates and times are in Asia/Kolkata.
- Only report what the tools return. Say so plainly when something is not available.
- Do not give seat availability, fares or booking help; the plugin has no such data.
- Include the source link from each result.
