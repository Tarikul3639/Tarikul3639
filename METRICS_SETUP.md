# GitHub Metrics Setup Instructions

This guide will help you set up GitHub Metrics for your profile repository.

## Prerequisites

- A GitHub account
- Admin access to your profile repository (Tarikul3639/Tarikul3639)

## Step 1: Generate a GitHub Personal Access Token

1. Go to your GitHub Settings: https://github.com/settings/tokens
2. Click on **"Generate new token"** → **"Generate new token (classic)"**
3. Give your token a descriptive name, e.g., `GitHub Metrics Token`
4. Set an expiration date (recommended: 90 days or No expiration for convenience)
5. Select the following scopes/permissions:
   - ✅ `public_repo` (under repo section) - Access public repositories
   - ✅ `read:user` - Read user profile data
   - ✅ `repo` (full control) - If you want to include private repository stats

6. Scroll down and click **"Generate token"**
7. **Important**: Copy the token immediately! You won't be able to see it again.

## Step 2: Add Token as Repository Secret

1. Go to your repository: https://github.com/Tarikul3639/Tarikul3639
2. Click on **"Settings"** tab
3. In the left sidebar, navigate to **"Secrets and variables"** → **"Actions"**
4. Click **"New repository secret"**
5. Enter the secret details:
   - **Name**: `METRICS_TOKEN` (must be exactly this name)
   - **Secret**: Paste the token you copied in Step 1
6. Click **"Add secret"**

## Step 3: Verify Workflow File

The workflow file should already be created at `.github/workflows/metrics.yml`. This file configures:

- **Daily automatic runs** at 00:00 UTC
- **Manual trigger** capability
- All metrics plugins including:
  - Base stats (repositories, commits, stars, followers)
  - Isometric calendar (full year)
  - Languages (most used and recently used)
  - Achievements (compact display)
  - Recent activity (last 5 activities)
  - Notable contributions
  - Coding habits with charts
  - Issues and PRs follow-up
  - Recently starred repositories
  - Starred topics with icons

## Step 4: Trigger the Workflow Manually (First Run)

1. Go to the **"Actions"** tab in your repository
2. In the left sidebar, click on **"Metrics"** workflow
3. Click the **"Run workflow"** button (on the right side)
4. Select the branch (usually `master` or `main`)
5. Click **"Run workflow"** to start the metrics generation

## Step 5: Wait for Completion

- The workflow typically takes 2-5 minutes to complete
- Once finished, a new file `github-metrics.svg` will be generated in your repository
- You can check the workflow run status in the Actions tab

## Step 6: View Your Metrics

After the workflow completes successfully, your metrics will be visible in your README.md file as an embedded SVG image.

## Troubleshooting

### Issue: Workflow fails with "Bad credentials"
**Solution**: Check that:
- The token was copied correctly without extra spaces
- The secret is named exactly `METRICS_TOKEN`
- The token hasn't expired
- The token has the required permissions (`public_repo`, `read:user`)

### Issue: Workflow fails with "Resource not accessible by integration"
**Solution**: 
- Ensure your token has the correct scopes
- Try regenerating the token with full `repo` access instead of just `public_repo`

### Issue: Metrics image doesn't appear in README
**Solution**: 
- Wait a few minutes for GitHub to process the file
- Check that `github-metrics.svg` exists in your repository root
- Try hard-refreshing your browser (Ctrl+F5 or Cmd+Shift+R)
- Ensure the image path in README.md is correct: `![Metrics](github-metrics.svg)`

### Issue: Some plugins show no data
**Solution**: 
- Some plugins require activity in specific areas (e.g., stars plugin needs starred repositories)
- Wait for the next automatic run (daily at 00:00 UTC)
- The metrics improve over time as you use GitHub more

### Issue: Token expired
**Solution**: 
- Generate a new token following Step 1
- Update the repository secret following Step 2
- Consider setting "No expiration" for the token if you want continuous updates

## Updating the Workflow

If you need to customize the metrics:

1. Edit `.github/workflows/metrics.yml`
2. Modify the plugin settings or add new plugins
3. Commit and push your changes
4. Manually trigger the workflow to see results immediately

## Additional Resources

- [Metrics Documentation](https://github.com/lowlighter/metrics)
- [Available Plugins](https://github.com/lowlighter/metrics#-plugins)
- [Plugin Configuration Examples](https://github.com/lowlighter/metrics/tree/master/.github/readme)

## Support

If you encounter issues not covered here:
1. Check the workflow logs in the Actions tab
2. Review the [Metrics repository issues](https://github.com/lowlighter/metrics/issues)
3. Ensure your token has the necessary permissions

---

**Note**: The workflow runs automatically every day at 00:00 UTC. You can also trigger it manually anytime from the Actions tab.
