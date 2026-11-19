# Vice content feeds

`vice_shorts.json` controls the Shorts tab. Add only videos uploaded to or licensed for your channel. Each video item must include `id`, `title`, `creator`, and the YouTube `youtubeId`.

`vice_tips.json` controls Tips & Tricks. Each item uses `id`, `category`, `title`, `summary`, and a `steps` array.

`giveaway_config.json` controls the public weekly announcement card in the Giveaway tab:

- `scheduleLabel` and `announcementTime` show when results are announced.
- `title`, `weekLabel`, and `message` control the announcement copy.
- `winners` accepts verified objects with `name` and `prize`. Leave it as an empty array until results have been reviewed.

Never add email addresses or other private participant data to this repository. Giveaway contact details are submitted to the private Google Apps Script/Sheets backend. Keep participant counts and entry activation out of these files until official rules and secure server validation are ready.
