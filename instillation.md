# Installation Guide

## Prerequisites

Before installing the Google Ads Bid Automation Script, ensure you have:

- ✅ Google Ads account with active campaigns
- ✅ Manual CPC bidding strategy enabled
- ✅ Conversion tracking set up (recommended)
- ✅ Admin access to Google Ads Scripts
- ✅ Valid email address for reports

## Step 1: Access Google Ads Scripts

1. **Log into Google Ads:**
   - Go to [ads.google.com](https://ads.google.com)
   - Select your Google Ads account

2. **Navigate to Scripts:**
   - Click "Tools & Settings" (wrench icon)
   - Under "Bulk Actions," click "Scripts"
   - Click the blue "+" button to create a new script

## Step 2: Upload the Script

1. **Copy Script Code:**
   - Open `google-ads-bid-automation.js` from this repository
   - Select all code (Ctrl+A / Cmd+A)
   - Copy to clipboard (Ctrl+C / Cmd+C)

2. **Paste into Google Ads:**
   - In the Google Ads Scripts editor, delete any existing code
   - Paste the bid automation script
   - Name your script: "Bid Automation - Production"

## Step 3: Configure Settings

Update these key settings in the `CONFIG` object:

```javascript
const CONFIG = {
  // REQUIRED: Update with your email
  REPORT_EMAIL: 'john@itallstartedwithaidea.com',
  
  // IMPORTANT: Start in testing mode
  DRY_RUN: true,
  
  // Adjust bid limits for your account
  MAX_BID_LIMIT: 10.00,     // Maximum bid per keyword
  MIN_BID_LIMIT: 0.25,      // Minimum bid per keyword
  
  // Target impression share (70% recommended)
  TARGET_TOP_OF_PAGE_IS: 0.70,
};
```

### Configuration Options

| Setting | Description | Recommended Value |
|---------|-------------|-------------------|
| `REPORT_EMAIL` | Email for automated reports | Your email address |
| `DRY_RUN` | Test mode (no actual changes) | `true` for testing |
| `TARGET_TOP_OF_PAGE_IS` | Target impression share | `0.70` (70%) |
| `MAX_BID_LIMIT` | Maximum bid per keyword | `10.00` |
| `BID_INCREASE_PERCENTAGE` | Bid increase amount | `0.15` (15%) |

## Step 4: Authorization

1. **Authorize Script:**
   - Click "Authorize" button
   - Sign in with Google account
   - Grant permissions for:
     - Access to Google Ads data
     - Email sending capabilities
     - Campaign modification rights

2. **Review Permissions:**
   - The script needs read/write access to campaigns
   - Email permissions for sending reports
   - No external data access required

## Step 5: Initial Testing

### Test Run 1: Dry Run Mode

1. **Ensure Testing Mode:**
   ```javascript
   DRY_RUN: true,
   ENABLE_DETAILED_LOGGING: true,
   ```

2. **Run Preview:**
   - Click "Preview" button
   - Wait for execution to complete (2-5 minutes)
   - Review logs for any errors

3. **Check Results:**
   - Look for "[DRY RUN]" messages in logs
   - Verify email report is sent
   - Confirm no actual bid changes occurred

### Test Run 2: Single Campaign

1. **Limit Scope for Testing:**
   ```javascript
   MAX_KEYWORDS_TO_ADJUST: 10,
   MIN_IMPRESSIONS_THRESHOLD: 20,
   ```

2. **Run Second Preview:**
   - Execute script again
   - Verify consistent results
   - Check email report accuracy

## Step 6: Budget Preparation

### Calculate Potential Spend Increase

**Before enabling live mode, estimate budget impact:**

1. **Review Current Bids:**
   - Note keywords with very low bids (e.g., $0.01)
   - Identify first page bid recommendations

2. **Calculate Increases:**
   - Keyword: "digital marketing agency"
   - Current bid: $0.01
   - Recommended: $4.20
   - Increase: 4,200%

3. **Adjust Daily Budgets:**
   - If current budget: $50/day
   - Potential new spend: $200-500/day
   - Recommended: Increase budget to $200/day initially

### Budget Safety Net

```javascript
// Conservative settings for initial go-live
CONFIG = {
  MAX_BID_LIMIT: 5.00,              // Lower max bid
  BID_INCREASE_PERCENTAGE: 0.10,    // Smaller increases
  TARGET_TOP_OF_PAGE_IS: 0.60,      // Lower target
}
```

## Step 7: Go Live

### Pre-Live Checklist

- [ ] Daily budgets increased appropriately
- [ ] Dry run tests completed successfully
- [ ] Email reports working correctly
- [ ] Team notified of automation launch
- [ ] Monitoring plan in place

### Enable Live Mode

1. **Update Configuration:**
   ```javascript
   DRY_RUN: false,
   ENABLE_DETAILED_LOGGING: false,
   ```

2. **First Live Run:**
   - Click "Run" button (not Preview)
   - Monitor execution closely
   - Check for any errors in logs

3. **Verify Changes:**
   - Go to Keywords tab in Google Ads
   - Confirm bid changes were applied
   - Review campaign performance

## Step 8: Schedule Automation

### Set Up Daily Runs

1. **Create Schedule:**
   - In Google Ads Scripts, click "Schedule"
   - Choose "Daily" frequency
   - Set time: 6:00 AM (recommended)
   - Time zone: Your account's time zone

2. **Schedule Settings:**
   ```
   Frequency: Daily
   Time: 06:00 AM
   Timezone: Eastern Time (or your preference)
   Email notifications: On failure
   ```

### Monitoring Schedule

**Week 1: Daily monitoring**
- Check email reports daily
- Review bid changes in Google Ads
- Monitor budget utilization
- Watch for conversion rate impacts

**Week 2-4: Regular monitoring**
- Review email reports 2-3x per week
- Adjust thresholds if needed
- Monitor overall account performance

**Month 2+: Maintenance mode**
- Weekly email report reviews
- Monthly threshold adjustments
- Quarterly performance analysis

## Step 9: Advanced Setup (Optional)

### Multiple Campaign Targeting

To run different settings for different campaigns:

```javascript
// Create separate scripts for different campaign types
// Script 1: Brand campaigns (conservative)
CONFIG.TARGET_TOP_OF_PAGE_IS = 0.80;
CONFIG.MAX_BID_LIMIT = 15.00;

// Script 2: Generic campaigns (aggressive)  
CONFIG.TARGET_TOP_OF_PAGE_IS = 0.60;
CONFIG.MAX_BID_LIMIT = 8.00;
```

### Custom Alerts

Add Slack or Teams integration:

```javascript
// Add after email sending
function sendSlackAlert(message) {
  // Your Slack webhook integration
}
```

## Troubleshooting Installation

### Common Issues

**Script won't authorize:**
- Ensure you have admin access to Google Ads account
- Try incognito/private browser window
- Clear browser cache and cookies

**No email reports received:**
- Check spam/junk folder
- Verify email address in CONFIG
- Test with alternative email address

**Script times out:**
- Reduce MAX_KEYWORDS_TO_ADJUST to 50
- Increase MIN_IMPRESSIONS_THRESHOLD to 100
- Disable detailed logging

### Getting Help

**Script Issues:**
- Email: john@itallstartedwithaidea.com
- Include: Error logs, account structure, configuration used

**Performance Questions:**
- Instagram: @_johnmwilliams
- Include: Before/after screenshots, specific campaigns affected

---

## Next Steps

After successful installation:

1. **Read the Main README.md** for usage guidelines
2. **Review CONFIGURATION.md** for advanced settings
3. **Check TROUBLESHOOTING.md** for common issues
4. **Monitor performance** using the email reports

**Success Metrics to Track:**
- ✅ Impression share improvements
- ✅ Maintained or improved conversion rates  
- ✅ Efficient budget utilization
- ✅ Consistent email report delivery
