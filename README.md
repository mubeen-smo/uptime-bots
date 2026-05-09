# uptime-bots

This repository contains uptime monitoring bots to keep web applications awake, preventing them from going to sleep on free hosting tiers.

## Keep Awake Workflow

The `.github/workflows/keep_awake.yml` file contains a GitHub Actions workflow that automatically pings your Streamlit app every 10 hours to keep it awake.

### Setup

1. Add your Streamlit app URL as a repository secret named `STREAMLIT_APP_URL`.
   - Go to your repository settings > Secrets and variables > Actions.
   - Create a new secret with the key `STREAMLIT_APP_URL` and value as your app's URL (e.g., `https://your-app.streamlit.app/`).

2. The workflow will run automatically on the schedule or can be triggered manually via the Actions tab.

### Manual Triggering

To manually trigger the keep awake workflow:

1. Go to the **Actions** tab in your GitHub repository.
2. Select the "Keep Streamlit App Awake" workflow from the list.
3. Click the **Run workflow** button (usually a play icon or "Run workflow" text).
4. Confirm by clicking **Run workflow** in the popup (no inputs required).

This is useful for testing the workflow or waking the app immediately.

### Workflow Details

- **Trigger**: Every 10 hours (cron: `0 */10 * * *`) or manual dispatch.
- **Action**: Sends a HEAD request to the app URL to wake it up if sleeping.
- **Runner**: Ubuntu latest.