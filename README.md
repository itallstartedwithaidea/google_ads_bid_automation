# Google Ads Bid Automation Script

**Created by John Williams ([@_johnmwilliams](https://instagram.com/_johnmwilliams))**  
Contact: [john@itallstartedwithaidea.com](mailto:john@itallstartedwithaidea.com)

## Overview

This Google Ads Script automatically optimizes manual bid amounts based on impression share metrics and generates comprehensive email reports with performance analytics. The script intelligently adjusts bids to achieve target top-of-page impression share while monitoring budget constraints and conversion performance.

## Features

### 🎯 **Intelligent Bid Optimization**
- Automatically adjusts manual CPC bids based on top-of-page impression share
- Uses Google's first page bid estimates for severely under-bidding keywords
- Considers conversion rate thresholds to avoid bidding on non-performing terms
- Implements safety limits and gradual optimization approach

### 📊 **Comprehensive Reporting**
- Dynamic HTML email reports with real campaign data
- Week-over-week performance comparisons
- Campaign-level performance breakdowns
- Top performing keyword adjustments tracking
- Actionable alerts and recommendations

### 🛡️ **Safety Features**
- Dry-run mode for testing without making changes
- Maximum bid limits and budget utilization monitoring
- Bidding strategy compatibility checking
- Error handling and rollback capabilities
- Execution time limits to prevent timeouts

### 🔧 **Advanced Monitoring**
- Budget constraint detection and alerts
- Quality Score impact analysis
- Competitor activity monitoring
- Conversion rate degradation warnings
- Campaign health scoring

## Quick Start

### 1. Installation

1. **Access Google Ads Scripts:**
   - Log into your Google Ads account
   - Navigate to Tools & Settings → Scripts
   - Click the "+" button to create a new script

2. **Upload the Script:**
   - Copy the contents of `google-ads-bid-automation.js`
   - Paste into the Google Ads Scripts editor
   - Name your script (e.g., "Bid Automation - Production")

3. **Configure Settings:**
   - Update the `CONFIG` object with your preferences
   - Set your email address in `REPORT_EMAIL`
   - Adjust target impression share thresholds
   - Set appropriate bid limits for your account

### 2. Configuration

```javascript
const CONFIG = {
  // Target impression share thresholds
  TARGET_TOP_OF_PAGE_IS: 0.70,        // 70% target
  TARGET_ABSOLUTE_TOP_IS: 0.30,       // 30% target
  
  // Bid adjustment parameters
  BID_INCREASE_PERCENTAGE: 0.15,      // 15% increase
  BID_DECREASE_PERCENTAGE: 0.10,      // 10% decrease
  MAX_BID_LIMIT: 10.00,               // $10 maximum bid
  MIN_BID_LIMIT: 0.25,                // $0.25 minimum bid
  
  // Email settings
  REPORT_EMAIL: 'your-email@domain.com',
  
  // Testing mode
  DRY_RUN: true                       // Set false for live changes
};
```

### 3. Testing

1. **Enable Dry-Run Mode:**
   ```javascript
   DRY_RUN: true
   ```

2. **Run Initial Test:**
   - Click "Preview" in Google Ads Scripts
   - Review the logs for proposed changes
   - Check email report for accuracy

3. **Validate Campaign Compatibility:**
   - Ensure campaigns use Manual CPC bidding
   - Verify sufficient budget for bid increases
   - Check keyword performance data availability

### 4. Go Live

1. **Increase Budgets First:**
   - Calculate potential spend increase from bid changes
   - Adjust daily budgets accordingly
   - Consider starting with subset of campaigns

2. **Enable Live Mode:**
   ```javascript
   DRY_RUN: false
   ```

3. **Schedule Automation:**
   - Set up daily runs at 6:00 AM (recommended)
   - Monitor performance for first week closely
   - Adjust thresholds based on results

## Campaign Requirements

### ✅ **Compatible Campaigns**
- Manual CPC bidding strategy
- Search campaign type
- Enabled keywords with sufficient impression data
- Conversion tracking enabled (recommended)

### ❌ **Incompatible Campaigns**
- Smart Bidding strategies (Target CPA, Target ROAS, etc.)
- Display/Video campaigns
- Automated bidding without manual override
- Campaigns with extremely limited budgets

## Understanding the Reports

### Key Metrics Explained

**Top of Page Impression Share (IS):**
- Percentage of times your ads appeared in top positions
- Target: 70% for competitive visibility
- Low IS = Need higher bids or better Quality Scores

**Budget Utilization:**
- Percentage of daily budget being spent
- >85% = Budget constrained, consider increasing
- <30% = Potential Quality Score or targeting issues

**Bid Change Percentage:**
- Average percentage change in keyword bids
- Positive = Increasing bids for more visibility
- Negative = Decreasing bids for efficiency

### Alert Types

🚨 **High Priority Alerts:**
- Conversion rate drops >8%
- Automated bidding conflicts
- Script execution errors

⚠️ **Medium Priority Alerts:**
- Budget constraints (>85% utilization)
- Low spend relative to budget
- Quality Score degradation

✅ **Success Alerts:**
- Keywords meeting target impression share
- Improved performance metrics
- Successful bid optimizations

## Advanced Configuration

### Custom Thresholds

```javascript
// Conservative approach
TARGET_TOP_OF_PAGE_IS: 0.60,
BID_INCREASE_PERCENTAGE: 0.10,

// Aggressive approach  
TARGET_TOP_OF_PAGE_IS: 0.80,
BID_INCREASE_PERCENTAGE: 0.25,

// Budget-conscious approach
MAX_BID_LIMIT: 5.00,
MIN_IMPRESSIONS_THRESHOLD: 100,
```

### Performance Optimization

```javascript
// For large accounts
MAX_KEYWORDS_TO_ADJUST: 500,
BATCH_SIZE: 100,

// For small accounts
MAX_KEYWORDS_TO_ADJUST: 50,
BATCH_SIZE: 25,
```

## Troubleshooting

### Common Issues

**Script Timeout:**
- Reduce `MAX_KEYWORDS_TO_ADJUST`
- Increase `BATCH_SIZE`
- Disable detailed logging

**No Bid Changes:**
- Check bidding strategy compatibility
- Verify keyword impression thresholds
- Review budget constraints

**High CPC Increases:**
- Lower `BID_INCREASE_PERCENTAGE`
- Reduce `MAX_BID_LIMIT`
- Focus on Quality Score improvements

**Email Reports Not Sending:**
- Verify email address in CONFIG
- Check Google Apps Script permissions
- Review execution logs for errors

### Debug Mode

Enable detailed logging:
```javascript
ENABLE_DETAILED_LOGGING: true,
DRY_RUN: true
```

### Support

For issues or questions:
- Email: [john@itallstartedwithaidea.com](mailto:john@itallstartedwithaidea.com)
- Instagram: [@_johnmwilliams](https://instagram.com/_johnmwilliams)

## Version History

- **v2.4.1** - Current version with enhanced error handling and real-time bid estimation
- **v2.3.0** - Added budget constraint monitoring and Quality Score alerts
- **v2.2.0** - Implemented dynamic email reporting with campaign-specific data
- **v2.1.0** - Added dry-run mode and safety features
- **v2.0.0** - Complete rewrite with impression share optimization

## License

Created by John Williams for itallstartedwithaidea.com  
Feel free to modify and distribute with attribution.

---

*This script is provided as-is. Always test in dry-run mode before making live changes to your Google Ads campaigns.*
