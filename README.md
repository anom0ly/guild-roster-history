# Guild Roster History

A one-page report of a guild's raid roster over time, built from Warcraft Logs (retail).

- **Roster for a tier:** everyone on a Mythic kill of that tier's final boss. One kill counts.
- **Longest-serving raiders:** ranked by the number of tiers with a Mythic final-boss kill in the guild, then by total kills.
- **Tier over tier:** who joined, who left and who stayed, compared with the previous tier.
- **Timeline:** players by tiers.
- **Step 1:** link alts to mains and exclude players (pugs, carries). A "1-kill only" filter helps find them.

Everything runs in your browser. Your Warcraft Logs sign-in, the fetched data, and your alt links and exclusions are stored only in this browser's local storage.

## Setup

1. **Turn on GitHub Pages:** Settings → Pages → Source: *Deploy from a branch*, Branch: `main` / `(root)`. The site will be at `https://anom0ly.github.io/guild-roster-history/`.
2. **Create a Warcraft Logs API client:** go to <https://www.warcraftlogs.com/api/clients/> and create a client with:
   - Name: `Guild Roster History`
   - Redirect URL: `https://anom0ly.github.io/guild-roster-history/`. This must match exactly, including the trailing slash.
   - Check **Public Client**. That way no client secret is needed.
3. **Paste the client ID** into `index.html`, near the top of the script:
   ```js
   const CONFIG = { clientId: "PASTE_YOUR_CLIENT_ID_HERE" };
   ```
   The client ID is not a secret. Commit the change.
4. Open the site, enter the guild name, realm slug (e.g. `area-52`) and region, then **Sign in with Warcraft Logs** and **Fetch guild logs**.

## Notes

- **Archived logs:** Warcraft Logs archives reports older than 2 years. Those only load if your account has a Gold or Platinum subscription. Otherwise they're counted as "couldn't be read".
- **Rate limit:** the API allows a limited number of points per hour. Progress is saved after each batch, so if you hit the limit, wait and press Fetch again. It picks up where it stopped.
- **Duplicate logs:** when several people upload the same raid, kills of the same boss within 10 minutes of each other are merged into one.
- **Final boss:** the last encounter Warcraft Logs lists for each raid zone.
