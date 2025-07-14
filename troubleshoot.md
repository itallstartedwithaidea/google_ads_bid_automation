# Troubleshooting Guide

## Common Issues and Solutions

This guide covers the most frequently encountered issues with the Google Ads Bid Automation Script and provides step-by-step solutions.

## Script Execution Issues

### ❌ Script Timeout Errors

**Problem:** Script execution stops with timeout error  
**Symptoms:**
```
Execution timeout: Script exceeded maximum execution time of 6 minutes
```

**Solutions:**
1. **Reduce keyword processing limit:**
   ```javascript
   MAX_KEYWORDS_TO_ADJUST: 50,  // Reduce from 200
   ```

2. **Increase batch size:**
   ```javascript
   BATCH_SIZE: 25,  // Reduce from 50
   ```

3. **Disable detailed logging:**
   ```javascript
   ENABLE_DETAILED_LOGGING: false,
   ```

4. **Reduce lookback period:**
   ```javascript
   LOOKBACK_DAYS: 3,  // Reduce from 7
   ```

### ❌ Authorization/Permission Errors

**Problem:** Script can't access Google Ads data  
**Symptoms:**
```
Authorization required: Please authorize this script to access your Google Ads account
```

**Solutions:**
1. **Re-authorize the script:**
   - Click "Authorize" in Google Ads Scripts
   - Sign in with correct Google account
   - Grant all requested permissions

2. **Check account access:**
   - Ensure you have admin access to the Google Ads account
   - Verify you're signed in with the correct Google account

3. **Clear browser cache:**
   - Clear cookies and cached data
   - Try using incognito/private browsing mode

### ❌ Invalid Field/Method Errors

**Problem:** Script fails with API method errors  
**Symptoms:**
```
TypeError: campaign.getBiddingStrategy is not a function
InputError: 'KeywordId' is not a valid field
```

**Solutions:**
1. **Update to latest script version:**
   - These errors are fixed in the current version
   - Replace old script with latest code

2. **Check Google Ads Scripts API version:**
   - Google occasionally updates API methods
   - Refer to current Google Ads Scripts documentation

## Bidding and Performance Issues

### ❌ No Bid Changes Occurring

**Problem:** Script runs successfully but doesn't modify any bids  
**Symptoms:**
- Email reports show 0 keywords modified
- Bids remain unchanged in Google Ads interface

**Root Causes & Solutions:**

1. **Automated bidding strategy:**
   ```javascript
   // Check campaign bidding strategy
   // Script will skip automated bidding campaigns
   ```
   **Fix:** Switch campaigns to Manual CPC bidding

2. **Insufficient impression data:**
   ```javascript
   MIN_IMPRESSIONS_THRESHOLD: 10,  // Lower from 20
   ```

3. **Conversion rate threshold too high:**
   ```javascript
   MIN_CONVERSION_RATE: 0.01,  // Lower from 0.02
   ```

4. **Target already achieved:**
   - Keywords may already be meeting impression share targets
   - Check current impression share vs targets

### ❌ Overly Aggressive Bid Increases

**Problem:** Bids increase too dramatically  
**Symptoms:**
- CPC increases by 500%+ overnight
- Daily spend exhausting budget too quickly

**Solutions:**
1. **Reduce bid increase percentage:**
   ```javascript
   BID_INCREASE_PERCENTAGE: 0.08,  // Reduce from 0.15
   ```

2. **Lower maximum bid limit:**
   ```javascript
   MAX_BID_LIMIT: 5.00,  // Reduce from 10.00
   ```

3. **Enable gradual optimization:**
   ```javascript
   // Add bid change limits per execution
   const maxBidIncrease = currentBid * 1.25; // Max 25% increase per run
   newBid = Math.min(newBid, maxBidIncrease);
   ```

### ❌ Budget Exhaustion

**Problem:** Daily budgets depleting too quickly  
**Symptoms:**
- "Budget constrained" alerts
- Campaigns stopping early in the day

**Solutions:**
1. **Increase daily budgets before bid optimization:**
   - Calculate potential spend increase
   - Increase budget by 2-3x initial amount

2. **Implement budget monitoring:**
   ```javascript
   // Add budget checks before bid increases
   if (budgetUtilization > 80) {
     // Skip bid increases
     return null;
   }
   ```

3. **Start with conservative settings:**
   ```javascript
   TARGET_TOP_OF_PAGE_IS: 0.60,  // Lower target
   MAX_BID_LIMIT: 3.00,          // Lower max bid
   ```

## Email and Reporting Issues

### ❌ Email Reports Not Received

**Problem:** Script runs but no email reports arrive  
**Symptoms
