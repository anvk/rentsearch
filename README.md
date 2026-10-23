# rentsearch

**A daily apartment hunt that runs itself.** Every morning Claude searches the rental sites for you and adds new listings to a Google Sheet. Each listing gets a star rating, the price, and how far it is to walk to the place you care about, such as your kid's school or your office.

**You don't need to be a developer.** There is no code to run and nothing to install beyond the Claude app. You copy a spreadsheet, paste one set of instructions into Claude, and fill in a few details about what you're looking for. That's it.

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

You now have the five tabs described above, empty and ready.

### 2. Make the rules yours (optional, can be done later)

- **rating rules** tab: the example rules give stars for a walk under 10 minutes, for a house-type rental, and for rent under 2,750. Change the numbers to suit you, or add your own rules. The instructions are on the right side of the tab.
- **search rules** tab: if you know a website page or a search that should be checked every day, add it here. The three rows there are examples; change or delete them.

### 3. Copy your spreadsheet's link

Copy the address from your browser's address bar while the spreadsheet is open. It looks like `https://docs.google.com/spreadsheets/d/...`. You'll paste it in step 5.

### 4. Connect Google Sheets to Claude

1. Open the Claude app and go to **Settings → Connectors**.
2. Find **Google Sheets** (or **Google Drive**) and click **Connect**.
3. Sign in with the Google account that owns your spreadsheet and allow access.

### 5. Create the daily task

1. In the Claude app, open **Cowork** and start a new **scheduled task**.
2. Name it, for example "Daily rent search".
3. Open [`prompt.md`](prompt.md), click the copy button at the top right of the grey box, and paste everything into the task's instructions.
4. At the very top of what you pasted, fill in **YOUR SEARCH**: your spreadsheet link from step 3, the place you want to live near and its address, the number of bedrooms, your highest rent, your longest walk, whether basement apartments are OK, the neighbourhoods to search, and the rental sites people use in your city. Replace everything in `[square brackets]`. If you don't know which sites to use, write "your choice".
5. Set it to run **daily** at a time that suits you, for example 7:00 in the morning.
6. Make sure the **Google Sheets** connector is turned on for this task.
7. Save the task.

### 6. Try it once

Run the task now instead of waiting for tomorrow (look for **Run now**). After a few minutes, open your spreadsheet: new listings should be in the **rent proposals** tab, and the **log** tab should have a line for today. If Claude says something in `[square brackets]` still needs filling in, edit the task and finish step 5.4.

### 7. Share it (optional)

In your spreadsheet, click **Share** (top right), add the email addresses of the people searching with you, and choose **Editor** so they can mark listings too. Claude keeps working in the same sheet, so everyone always sees the latest list.

## Using it day to day

- **New listings** have "Yes" in the _Is New_ column. Click a listing's name to open its page.
- **Don't like one?** Type `yes` in its _skipped_ column and say why in _skipped reason_, for example "too far" or "too noisy, on a busy road". The row turns red and moves down. Claude also learns from your reasons and leaves similar listings out from then on.
- **Claude left out a good one?** In the **bot skipped** tab, type `yes` in _bot was wrong_ and add a comment. The next run moves it to the main list and adjusts its rule.
- **A listing is gone?** Claude marks it "No" in _still available_ when the ad says it's rented or disappears. It never deletes anything.
- **Want different stars?** Change the **rating rules**; ratings update right away.
- **Read the log** for a daily summary, including anything that needs your attention.

## Good to know

- Sites that need a login, such as Facebook Marketplace, can't be searched by Claude. Many private landlords post there, so check them by hand.
- Walk times are estimates from straight-line distance, not real walking routes.
- An ad can stay online after the place is rented. "Yes" in _still available_ means the ad is still up, not that the landlord has confirmed it.
- Each run uses some of your Claude plan's usage.

## License

[MIT](LICENSE)
