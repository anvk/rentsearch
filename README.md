# rentsearch

**A daily apartment hunt that runs itself.** Every morning Claude searches the rental sites for you and adds new listings to a Google Sheet. Each listing gets a star rating, the price, and how far it is to walk to the place you care about, such as your kid's school or your office.

**You don't need to be a developer.** There is no code to run and nothing to install beyond the Claude app. You import a spreadsheet, then have a short chat with Claude about what you're looking for, and it sets up the rest: the rental sites for your area, the streets to watch and the star ratings. Then you paste the result into a daily task. That's it.

**Made for sharing.** The results live in an ordinary Google Sheet, so you can share it with your partner, family or realtor. Everyone sees the same list, can mark the places they don't like, and Claude learns from those choices.

## What you get

A Google Sheet with five tabs that Claude keeps up to date every day:

| Tab                              | What it's for                                                                                                                                                         |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **rent proposals**               | The main list. New listings are marked "Yes" in the _Is New_ column. Listings that are gone, or that you skipped, turn red and move to the bottom.                    |
| **rent proposals - bot skipped** | Listings Claude found but left out, with the reason (for example "too far, like the ones you skipped"). If Claude got it wrong, say so and it moves the listing back. |
| **rating rules**                 | How the stars are given: for example 2 stars for a short walk, 1 star for a lower price. Change a rule and every rating updates at once.                              |
| **search rules**                 | Extra websites, searches or streets you want checked every day, on top of Claude's own search.                                                                        |
| **log**                          | One line per day: what was added, what's no longer available, and anything that needs your attention.                                                                 |

## What you need

- A **Google account** (for Google Sheets).
- A **paid Claude plan** (Pro or higher), so Claude can run a task on a schedule.
- The **Claude desktop app** for Mac or Windows, from [claude.ai/download](https://claude.ai/download).

## Setup, step by step

It takes about 15 minutes, and you only do it once.

### 1. Get the spreadsheet

1. Download the template: open [`rent-search-template.xlsx`](rent-search-template.xlsx) and click the **Download** button (the arrow pointing down, at the top right of the page).
2. Go to [sheets.google.com](https://sheets.google.com) and click **Blank spreadsheet**.
3. In the new spreadsheet, click **File → Import → Upload**, and choose the file you just downloaded.
4. Under _Import location_, pick **Replace spreadsheet**, then click **Import data**.
5. Click the title at the top left ("Untitled spreadsheet") and give it a name, for example "Our rent search".
6. Copy the address from your browser's address bar. It looks like `https://docs.google.com/spreadsheets/d/...`, and Claude will ask for it in step 3.

### 2. Connect Google Sheets to Claude

1. Open the Claude app and go to **Settings → Connectors**.
2. Find **Google Sheets** (or **Google Drive**) and click **Connect**.
3. Sign in with the Google account that owns your spreadsheet and allow access.

### 3. Set up your search with Claude

1. In the Claude app, start a **new chat**.
2. Open [`setup-helper.md`](setup-helper.md), click the copy button at the top right of the grey box, paste it into the chat and send it.
3. Answer Claude's questions: the place you want to live near, bedrooms, budget, how far you'd walk, and what matters to you. Claude finds the rental sites and streets for your area, shows you its plan, and fills in your spreadsheet's **search rules** and **rating rules** once you say yes.
4. At the end, Claude gives you a short box that starts with **YOUR SEARCH**. Copy it.

Prefer to do it by hand? Copy the empty YOUR SEARCH box from [`prompt.md`](prompt.md) and replace everything in `[square brackets]` yourself.

### 4. Create the daily task

1. In the Claude app, open **Cowork** and start a new **scheduled task**. Name it, for example "Daily rent search".
2. Paste your **YOUR SEARCH** box from step 3 into the task's instructions.
3. Open [`prompt.md`](prompt.md), copy the second box (**the daily instructions**), and paste it below YOUR SEARCH.
4. Set it to run **daily** at a time that suits you, for example 7:00 in the morning.
5. Make sure the **Google Sheets** connector is turned on for this task, then save it.

### 5. Try it once

Run the task now instead of waiting for tomorrow (look for **Run now**). After a few minutes, open your spreadsheet: new listings should be in the **rent proposals** tab, and the **log** tab should have a line for today.

### 6. Share it (optional)

In your spreadsheet, click **Share** (top right), add the email addresses of the people searching with you, and choose **Editor** so they can mark listings too. Claude keeps working in the same sheet, so everyone always sees the latest list.

### Changing your search later

Run the setup helper again in a new chat, for example to raise your budget or add a neighbourhood. It shows your current settings, changes what you ask, and gives you a new YOUR SEARCH box. Open your daily task and replace its YOUR SEARCH part with the new one.

## Using it day to day

- **New listings** have "Yes" in the _Is New_ column. Click a listing's name to open its page.
- **Don't like one?** Type `yes` in its _skipped_ column and say why in _skipped reason_, for example "too far" or "too noisy, on a busy road". The row turns red and moves down. Claude also learns from your reasons and leaves similar listings out from then on.
- **Claude left out a good one?** In the **bot skipped** tab, type `yes` in _bot was wrong_ and add a comment. The next run moves it to the main list and adjusts its rule.
- **A listing is gone?** Claude marks it "No" in _still available_ when the ad says it's rented or disappears. It never deletes anything.
- **Want different stars?** Change the **rating rules** tab yourself, or ask the setup helper; ratings update right away.
- **Read the log** for a daily summary, including anything that needs your attention.

## Good to know

- Sites that need a login, such as Facebook Marketplace, can't be searched by Claude. Many private landlords post there, so check them by hand.
- Walk times are estimates from straight-line distance, not real walking routes.
- An ad can stay online after the place is rented. "Yes" in _still available_ means the ad is still up, not that the landlord has confirmed it.
- Each run uses some of your Claude plan's usage.

## License

[MIT](LICENSE)
