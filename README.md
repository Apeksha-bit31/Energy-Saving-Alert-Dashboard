# Energy-Saving-Alert-Dashboard
I’ve built the Energy Saving Alert Dashboard as a mobile-first page. It finds 13 alerts across the 30 test rows. I checked the rule counts . The notebook’s rule cells are blank, so I wrote three rules in one config block at the top of the page’s script. They are mutually exclusive, and each is triggered by more than one test row. 
Swap in your own rules there when you have them.
Rule	Condition	Rows triggered
1. Appliance Peak Shift	Dishwasher running during the Peak tariff	5
2. Peak-Hour HVAC	Heating or cooling during Peak, dishwasher off	6
3. Over-Cooling	Cooling while indoor temperature is at or below the cooling setpoint, Off-Peak	2

What’s on the page:

Layout: The latest alert sits on top as a large card, with a collapsible Archived alerts section below it. Each rule has its own color. The page has both light and dark themes.
Alert cards: Each card shows the timestamp, tariff, HVAC mode, indoor and outdoor temperature, the device usage in kWh (with the setpoint on HVAC alerts), the alert message and an italic tip. The tips are static text I wrote, one per triggered row, and they quote values from that row.
Timestamps: Alerts are sorted by the timestamp column. Two triggered rows carry the “Date/timestamp mismatch” note: 26 Jun 2025 18:00 (its date column says 28 Jun 2026) and 9 Jul 2026 22:00 (its hour column says 10).
Timezone: The data has no timezone, so times show as recorded. I didn’t assume IST or any other zone.
In a local headless-browser test, all 14 views opened, the on/off switch worked, and a phone-width check showed no sideways scrolling. I haven’t viewed the live page itself. The test showed one “Failed to load resource” console error. I think it’s the blocked font request from my test setup, but I didn’t confirm that.

What’s new on the home page

Test data icon: The “Test data” button at the top is now clickable. It opens a table of all 30 readings, newest first. It has filters for All, With alert and No alert. It also shows which rule each alert came from and flags date or hour mismatches.
Energy Alerts switch: The switch sits near the top of the home page, and its setting is remembered in your browser. While it’s off, the alert, trigger-time and tip pages show a “Turn on Energy Alerts” message, and the latest-alert preview is hidden. The appliance, rules, usage and data-check pages stay available.
My appliances: Tap HVAC, Dishwasher, Washer-dryer or Robot vacuum. Each page shows:
how often it ran in the test data
its kWh and share of test energy
a time-of-day usage chart from your Jan–Aug 2025 history
its recent readings
a suggested run time
Run-time advice: There’s also a new tile with the advice for all four appliances in one place.

Suggested run times come from your 5,832-row history.

Dishwasher: 1 cycle a day, started at 22:00 or later. 66% of cycles currently run in Peak, which is an estimated $11.21 over the period.
Washer-dryer: One 3-hour block between 10:00 and 15:00. That window was Off-Peak in every month of the history.
Robot vacuum: No change. It already runs 1 hour a day at 14:00, always Off-Peak.
HVAC: Keep it near 14 hours a day, but move 1 hour out of Peak. That is an estimated $22.92, assuming the hour just moves to Off-Peak.

The savings figures only reflect the price gap between Peak and Off-Peak. Peak hours change by season in the history, and a few test readings are labelled Peak at hours the history calls Off-Peak. The advice pages tell the user to check the live tariff before moving a cycle.
It has a bottom tab bar with five tabs and a row of options at the top of each section. I tested all 20 screens in a headless browser at phone width and none scrolled sideways. I looked at screenshots of the Live replay and Dashboard Overview screens. I didn’t see the page on a real phone, and the icons were stubbed out in my test, so I haven’t seen them render.

Bottom tabs and their options

Tab	Options
Home	Energy Alerts switch, latest alert, appliance and shortcut tiles, Test data button
Alerts	Live, Latest, All, Times, Tips
Advice	Run time, Best times, Savings, Rules
Dashboard	Overview, Usage, Test data, Checks
Appliances	My appliances, Compare, plus a page for each appliance

New screens

Live: It replays the 30 test readings in time order and adds each alert to a feed as it fires. It has Play, Pause and Restart, and it starts automatically when you open it. It is a replay, not a live sensor feed, and the page says so. A real feed would need a live data source.
Best times: Peak hours by season, shown as 24-hour strips, with the best time window for each appliance.
Savings: Estimated savings from following the run-time advice, about $35.34 in total over Jan–Aug 2025. The figure only reflects the price gap between Peak and Off-Peak.
Dashboard Overview: Total energy, cost, energy by appliance, alerts by rule, energy per reading and the Peak versus Off-Peak split.
Compare: The four appliances side by side.
Other changes
I fixed a bug where some cards were missing their rule colors.
The five tabs and the sub-options replace the old tile menu on the home page.
Copyright (c) 2026 Apeksha-bit31/Energy-Saving-Alert-Dashboard. All rights reserved.
