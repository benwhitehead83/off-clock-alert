# Runbook: reading the travel planning sheet

File: `file:///b!4aIh5XqNR0695sSZ61VoIePqFH1JiRlFjz4D0FKknncs6HyD3wh1RKd-1kfaCPWe/80 On_Off_sites/Global OPS_Business Travel Planning.xlsx`
(read with `read_resource`; sharepoint_search only surfaces the stale "(Backup)" copy from 2023 - ignore it).

- The output is huge and the date header row (row 8) is truncated, so save-to-file and parse with python (`-I`).
- Sheet "Travel Planning": one column per day, **column index 4 (0-based, tab-separated) = 5 Jun 2023**, +1 per day.
  Date -> index = 4 + (date - 2023-06-05).days. Verified: 22 Oct 2026 = index 1239 = column AUR.
- Ben's row is the line starting `Ben Whitehead` (line 13 of the saved text). Read the cell for today's local date.
- Never conclude "no 2026 data": the sheet runs to 2026 and beyond.

## Cell codes (inferred, confirm with Ben)
The real legend is in cells A70:C82 of sheet "Travel Planning", but the read_resource dump does not include those rows
(it jumps from row ~71 to the formulas list). Replace the guesses below once the legend text is available.
Site-style letters: S = Szczecin (SZZ), C = Columbus (CMH, US Eastern), K = Cologne (CGN), W/M/P/F other European sites,
U = holiday, x/X/. = office/home-type days, lowercase = tentative. Free-text cells ("PRO Visit CGN") are notes.
Ben's plan: C 21-29 Oct 2026, c 9-26 Nov and 7-20 Dec 2026.
Blank cell = default home base, Germany (Europe/Berlin).

## Time zones
Germany/Poland Europe/Berlin (CEST UTC+2 until 25 Oct 2026, then CET UTC+1); Columbus America/New_York (EDT UTC-4 until 1 Nov 2026, then EST UTC-5).
Off-clock = 21:00-08:00 local, all of Sat/Sun. Outside that: do nothing and send no notification.
