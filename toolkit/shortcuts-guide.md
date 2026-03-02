# Siri Shortcuts — Property Automation Recipes

Build these in the **Shortcuts** app on your iPhone 17 Pro. Each one saves you 5-15 minutes per use.

---

## 1. Daily Property Brief

**Trigger**: Morning automation (6:30 AM) or "Hey Siri, property brief"

**What it does**:
1. Gets today's weather in Phuket (important for outdoor viewings)
2. Gets current THB exchange rates (USD, EUR, GBP, RUB, CNY)
3. Shows today's calendar events (viewings)
4. Opens your GitHub Issues (pending tasks)

**How to build**:
```
Shortcut Steps:
1. Get Weather Forecast → Location: Phuket
2. Get Contents of URL → https://api.exchangerate-api.com/v4/latest/THB
3. Find Calendar Events → Date: Today, Calendar: Viewings
4. Show Results:
   - Weather summary
   - Key exchange rates
   - Today's viewings list
5. Open URL → GitHub Domovoy issues page
```

**Pro tip**: Set this as a morning automation: Settings → Shortcuts → Automation → Time of Day → 6:30 AM

---

## 2. Property Quick Capture

**Trigger**: Action Button or "Hey Siri, property capture"

**What it does**:
1. Asks for property name
2. Opens Camera in Photo mode (ProRAW)
3. After you close camera, asks: "Start LiDAR scan?"
4. Opens Polycam if yes
5. Creates a note with property name, date, location
6. Saves everything to a folder named after the property

**How to build**:
```
Shortcut Steps:
1. Ask for Input → "Property name?"  → Save to variable: PropertyName
2. Get Current Location → Save to variable: Location
3. Create Folder → in iCloud Drive/Domovoy/Properties/[PropertyName]-[Date]
4. Open Camera App
5. Wait to Return (camera closes when you're done)
6. Ask: "Start LiDAR scan?"
7. If Yes → Open App: Polycam
8. Create Note:
   Title: [PropertyName] - [Date]
   Body: Location: [Location]
         Time: [Current Time]
         Zone:
         Photos: Captured
         LiDAR: Yes/No
         Notes:
```

---

## 3. Property Wrap-Up

**Trigger**: "Hey Siri, property wrap up" (run after leaving a viewing)

**What it does**:
1. Asks: "Property name?" (or select from recent)
2. Gets your last 30 minutes of photos
3. Gets your last 30 minutes of voice memos
4. Counts the media captured
5. Creates a summary note
6. Reminds you to sync Ray-Ban Meta 2 footage

**How to build**:
```
Shortcut Steps:
1. Ask for Input → "Which property?" → Save to variable: PropertyName
2. Find Photos → Taken in Last 30 Minutes → Save to variable: Photos
3. Count [Photos] → Save to variable: PhotoCount
4. Find Voice Memos → Created in Last 30 Minutes
5. Show Alert:
   "[PropertyName] Viewing Complete
   Photos captured: [PhotoCount]

   Don't forget:
   - Sync Ray-Ban Meta 2 footage (open Meta View)
   - Review voice notes
   - Rate the property in inspection checklist"
6. Open App: Meta View (to sync glasses footage)
7. Create Reminder: "Process [PropertyName] media and listing" → Tomorrow 9 AM
```

---

## 4. Send Property Card

**Trigger**: "Hey Siri, send property card" or Share Sheet

**What it does**:
1. Asks which property
2. Selects best 5 photos from that property folder
3. Compiles a quick summary card
4. Asks: Send via WhatsApp / Line / Email
5. Sends with a formatted message

**How to build**:
```
Shortcut Steps:
1. Ask for Input → "Property name?"
2. Get files from: iCloud Drive/Domovoy/Properties/[PropertyName]
3. Select Photos → Limit to 5
4. Create text:
   "🏠 [PropertyName]
   Zone: [zone]
   Beds: [beds] | Price: [price] THB/mo
   School: [nearest school] ([distance] min)

   Domovoy — Luxury Family Housing, Phuket"
5. Choose from Menu: WhatsApp / Line / Email
6. Share via selected app with photos + text
```

---

## 5. Expense Tracker (Viewing Day)

**Trigger**: "Hey Siri, log expense"

**What it does**:
1. Asks: Amount (THB)
2. Asks: Category (Fuel / Food / Parking / Tolls / Client Lunch / Other)
3. Logs to a Numbers/Google Sheet with date, amount, category
4. Running total for the day/month

**How to build**:
```
Shortcut Steps:
1. Ask for Input → "Amount in THB?" (Number)
2. Choose from Menu → Fuel / Food / Parking / Tolls / Client Lunch / Other
3. Get Current Date
4. Add Row to Google Sheet or Numbers file:
   Date | Amount | Category | Running Total
5. Show notification: "[Category]: [Amount] THB logged"
```

---

## 6. Client Follow-Up Reminder

**Trigger**: "Hey Siri, follow up with client"

**What it does**:
1. Asks: Client name
2. Asks: Follow-up in how many days? (1/3/7)
3. Creates a reminder with the client's name
4. Optionally drafts a follow-up message template

**How to build**:
```
Shortcut Steps:
1. Ask for Input → "Client name?"
2. Choose from Menu → 1 day / 3 days / 1 week
3. Create Reminder:
   Title: "Follow up with [Client] about property viewing"
   Date: [Selected timeframe from now]
   Notes: "Suggested message:
   Hi [Client], I hope you're well! Following up on the properties
   we viewed. Would you like to schedule a second viewing or shall
   I find some additional options? Best, [Your name]"
4. Show notification: "Reminder set for [date]"
```

---

## 7. Exchange Rate Calculator

**Trigger**: "Hey Siri, convert to Thai baht"

**What it does**:
1. Asks: Amount
2. Asks: From which currency? (USD/EUR/GBP/RUB/CNY/AUD)
3. Gets live exchange rate
4. Shows the THB equivalent
5. Also shows monthly rent equivalent (useful during viewings)

**How to build**:
```
Shortcut Steps:
1. Ask for Input → "Amount?" (Number)
2. Choose from Menu → USD / EUR / GBP / RUB / CNY / AUD
3. Get Contents of URL → exchange rate API
4. Calculate: Amount × Rate = THB result
5. Show Result:
   "[Amount] [Currency] = [Result] THB

   At this rate:
   30,000 THB/mo = [reverse calc] [Currency]/mo
   50,000 THB/mo = [reverse calc] [Currency]/mo
   80,000 THB/mo = [reverse calc] [Currency]/mo"
```

---

## 8. School Run Timer

**Trigger**: "Hey Siri, time the school run"

**What it does**:
1. Asks: Starting from? (property name or current location)
2. Asks: Going to? (list of Phuket schools)
3. Starts a timer
4. When you arrive and say "Hey Siri, I arrived" → stops timer
5. Logs the route time with date, time of day, and traffic conditions

**Why**: Google Maps estimates don't reflect actual Phuket traffic. Real data from real drives is gold for family recommendations.

**How to build**:
```
Shortcut Steps:
1. Ask for Input → "Starting from?"
2. Choose from List → [List of Phuket schools]
3. Get Current Date + Time
4. Start Timer (or log start time)
5. Show notification: "Driving to [School]. Say 'Hey Siri, I arrived' when done."

--- Separate Shortcut: "I arrived" ---
1. Get start time from Data Store
2. Calculate elapsed time
3. Add Row to spreadsheet:
   Date | Time | From | To | Duration | Day of Week
4. Show: "School run: [Duration] minutes on a [Day]"
```

---

## Automation Triggers (Set Once, Run Forever)

### Location-Based
| Location | Trigger |
|----------|---------|
| Arrive at a property | Open Camera + start "Property Quick Capture" |
| Leave a property | Run "Property Wrap-Up" |
| Arrive at office | Show today's GitHub Issues |
| Arrive at school | Start "School Run Timer" log |

### Time-Based
| Time | Trigger |
|------|---------|
| 6:30 AM daily | "Daily Property Brief" |
| 8 PM daily | "Have you synced all media from today?" reminder |
| Friday 5 PM | "Weekly property review" reminder |
| Monday 9 AM | Create GitHub Issue: weekly review checklist |

### App-Based
| App Opens | Trigger |
|-----------|---------|
| Camera | Switch to "Property Viewing" Focus mode |
| Polycam | Turn on "Do Not Disturb" |
| Line / WhatsApp | Exit Focus mode (allow messages) |

---

## NFC Tag Shortcuts

Buy cheap NFC tags (~50 THB for 10) and program them:

| Tag Location | What It Triggers |
|-------------|-----------------|
| **Car dashboard** | Opens navigation to next viewing (from Calendar) |
| **Property folder/clipboard** | "Property Quick Capture" shortcut |
| **Office desk** | "Daily Property Brief" |
| **Business card** | Opens your WhatsApp/Line contact for clients to tap |
| **Key box** | Logs which property keys you took |

**How**: Shortcuts app → Automation → NFC → Scan tag → Assign shortcut

---

## Building Tips

1. **Start simple** — build shortcut #1 and #2 first, add others as you feel the need
2. **Test each one** 3 times before relying on it in the field
3. **Use variables** — name them clearly (PropertyName, not variable1)
4. **iCloud sync** — Shortcuts sync across devices, build on any Apple device
5. **Share shortcuts** — if you have a team, share via iCloud links
6. **Backup** — Shortcuts are backed up in iCloud, but export important ones as files too
