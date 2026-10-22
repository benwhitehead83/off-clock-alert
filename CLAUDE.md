# Runbook: reading the travel planning sheet

File: `file:///b!4aIh5XqNR0695sSZ61VoIePqFH1JiRlFjz4D0FKknncs6HyD3wh1RKd-1kfaCPWe/80 On_Off_sites/Global OPS_Business Travel Planning.xlsx`
(read with `read_resource`; sharepoint_search only surfaces the stale "(Backup)" copy from 2023 - ignore it).

- The output is huge and the date header row (row 8) is truncated, so save-to-file and parse with python (`-I`).
- Sheet "Travel Planning": one column per day, **column index 4 (0-based, tab-separated) = 5 Jun 2023**, +1 per day.
  Date -> index = 4 + (date - 2023-06-05).days. Verified: 22 Oct 2026 = index 1239 = column AUR.
- Ben's row is the line starting `Ben Whitehead` (line 13 of the saved text). Read the cell for today's local date.
- Never conclude "no 2026 data": the sheet runs to 2026 and beyond.

## Cell codes (legend from A70:C82; upper = fixed, lower = planned, both count)
s/S Szczecin (Europe/Warsaw), c/C Columbus (America/New_York), m/M Munich (Europe/Berlin), p/P Phoenix (America/Phoenix, UTC-7, no DST),
k/K Cologne (Europe/Berlin), w/W Wolfen (Europe/Berlin), r/R Riga (Europe/Riga, +1h vs Berlin), f/F Conference/Fair (see "Trade Fairs" sheet city for the zone),
u/U Vacation, h/H Home Office, x/X Other (location unknown: assume Europe/Berlin), blank/"." = Europe/Berlin, public holiday = orange fill (not visible in dump).
Free-text cells ("PRO Visit CGN") are notes. Ben's plan: C 21-29 Oct 2026, c 9-26 Nov and 7-20 Dec 2026.
Vacation: still apply off-clock hours using the last known / home zone (Europe/Berlin if unclear).

## Time zones
Germany/Poland Europe/Berlin (Riga +1h) (CEST UTC+2 until 25 Oct 2026, then CET UTC+1); Columbus America/New_York (EDT UTC-4 until 1 Nov 2026, then EST UTC-5).
Off-clock = 21:00-08:00 local, all of Sat/Sun. Outside that: do nothing and send no notification.
