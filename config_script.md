# Configuration Guide

## Overview

This guide covers all configuration options for the Google Ads Bid Automation Script. Understanding these settings allows you to customize the script's behavior for your specific account needs and performance goals.

## Core Configuration Object

The script uses a single `CONFIG` object containing all customizable settings:

```javascript
const CONFIG = {
  // Target impression share thresholds
  TARGET_TOP_OF_PAGE_IS: 0.70,
  TARGET_ABSOLUTE_TOP_IS: 0.30,
  
  // Bid adjustment parameters
  BID_INCREASE_PERCENTAGE: 0.15,
  BID_DECREASE_PERCENTAGE: 0.10,
  MAX_BID_LIMIT: 10.00,
  MIN_BID_LIMIT: 0.25,
  
  // Performance thresholds
  MIN_CONVERSION_RATE: 0.02,
  MAX_CPC_INCREASE: 0.50,
  MIN_IMPRESSIONS_THRESHOLD: 20,
  
  // Email settings
  REPORT_EMAIL: 'john@itallstartedwithaidea.com',
  REPORT_SUBJECT: 'Google Ads Bid Automation Report',
  
  // Safety limits
  MAX_KEYWORDS_TO_ADJUST: 200,
  LOOKBACK_DAYS: 7,
  
  // Reporting
  ENABLE_EMAIL_REPORTS: true,
  ENABLE_DETAILED_LOGGING: false,
  
  // Testing mode
  DRY_RUN: false,
  
  // Script execution limits
  MAX_EXECUTION_TIME_MINUTES: 4,
  BATCH_SIZE: 50
};
```

## Impression Share Settings

### TARGET_TOP_OF_PAGE_IS
**Default:** `0.70` (70%)  
**Range:** `0.30` - `0.95`  
**Description:** Target percentage for top-of-page impression share

```javascript
// Conservative approach - easier to achieve
TARGET_TOP_OF_PAGE_IS: 0.60,

// Aggressive approach - maximum visibility
TARGET_TOP_OF_PAGE_IS: 0.85,

// Balanced approach - good visibility with efficiency
TARGET_TOP_OF_PAGE_IS: 0.70,
```

**Considerations:**
- Higher targets require more aggressive bidding
- Consider your industry competitiveness
- Balance visibility with cost efficiency

### TARGET_ABSOLUTE_TOP_IS
**Default:** `0.30` (30%)  
**Range:** `0.10` - `0.60`  
**Description:** Target for absolute top position (above all other ads)

```javascript
// Brand protection focus
TARGET_ABSOLUTE_TOP_IS: 0.50,

// Cost efficiency focus
TARGET_ABSOLUTE_TOP_IS: 0.20,

// Balanced approach
TARGET_ABSOLUTE_TOP_IS: 0.30,
```

## Bid Adjustment Parameters

### BID_INCREASE_PERCENTAGE
**Default:** `0.15` (15%)  
**Range:** `0.05` - `0.50`  
**Description:** Percentage increase for underperforming keywords

```javascript
// Conservative increases (5-10%)
BID_INCREASE_PERCENTAGE: 0.08,

// Moderate increases (15-20%)
BID_INCREASE_PERCENTAGE: 0.18,

// Aggressive increases (25-50%)
BID_INCREASE_PERCENTAGE: 0.35,
```

**Use Cases:**
- **Conservative:** Mature accounts with stable performance
- **Moderate:** Most accounts with room for growth
- **Aggressive:** New accounts or highly competitive industries

### BID_DECREASE_PERCENTAGE
**Default:** `0.10` (10%)  
**Range:** `0.05` - `0.25`  
**Description:** Percentage decrease for over-performing keywords

```javascript
// Gentle decreases
BID_DECREASE_PERCENTAGE: 0.05,

// Standard decreases
BID_DECREASE_PERCENTAGE: 0.10,

// Aggressive decreases
BID_DECREASE_PERCENTAGE: 0.20,
```

### MAX_BID_LIMIT / MIN_BID_LIMIT
**Max Default:** `10.00`  
**Min Default:** `0.25`  
**Description:** Absolute bid boundaries

```javascript
// Budget-conscious account
MAX_BID_LIMIT: 5.00,
MIN_BID_LIMIT: 0.10,

// Premium service account
MAX_BID_LIMIT: 25.00,
MIN_BID_LIMIT: 1.00,

// Enterprise account
MAX_BID_LIMIT: 50.00,
MIN_BID_LIMIT: 2.00,
```

## Performance Thresholds

### MIN_CONVERSION_RATE
**Default:** `0.02` (2%)  
**Range:** `0.01` - `0.10`  
**Description:** Minimum conversion rate required for bid increases

```javascript
// Lead generation (lower conversion rates)
MIN_CONVERSION_RATE: 0.01,

// E-commerce (moderate conversion rates)
MIN_CONVERSION_RATE: 0.025,

// High-value services (higher conversion rates expected)
MIN_CONVERSION_RATE: 0.05,
```

### MIN_IMPRESSIONS_THRESHOLD
**Default:** `20`  
**Range:** `10` - `500`  
**Description:** Minimum impressions required for keyword optimization

```javascript
// Low-volume accounts
MIN_IMPRESSIONS_THRESHOLD: 10,

// Standard accounts
MIN_IMPRESSIONS_THRESHOLD: 50,

// High-volume accounts
MIN_IMPRESSIONS_THRESHOLD: 200,
```

## Email and Reporting

### Email Configuration
```javascript
// Basic email settings
REPORT_EMAIL: 'your-email@domain.com',
REPORT_SUBJECT: 'Google Ads Bid Automation Report',

// Multiple recipients
REPORT_EMAIL: 'manager@company.com,analyst@company.com',

// Custom subject with date
REPORT_SUBJECT: 'PPC Automation Report - ' + new Date().toLocaleDateString(),
```

### Reporting Options
```javascript
// Minimal reporting
ENABLE_EMAIL_REPORTS: true,
ENABLE_DETAILED_LOGGING: false,

// Comprehensive reporting  
ENABLE_EMAIL_REPORTS: true,
ENABLE_DETAILED_LOGGING: true,

// No email reports (logging only)
ENABLE_EMAIL_REPORTS: false,
ENABLE_DETAILED_LOGGING: true,
```

## Safety and Execution Limits

### Script Performance
```javascript
// Large account settings
MAX_KEYWORDS_TO_ADJUST: 500,
MAX_EXECUTION_TIME_MINUTES: 5,
BATCH_SIZE: 100,

// Small account settings
MAX_KEYWORDS_TO_ADJUST: 50,
MAX_EXECUTION_TIME_MINUTES: 2,
BATCH_SIZE: 25,

// Ultra-conservative settings
MAX_KEYWORDS_TO_ADJUST: 20,
MAX_EXECUTION_TIME_MINUTES: 1,
BATCH_SIZE: 10,
```

### Data Collection Period
```javascript
// Short-term optimization (faster response)
LOOKBACK_DAYS: 3,

// Standard optimization (balanced approach)
LOOKBACK_DAYS: 7,

// Long-term optimization (stable trends)
LOOKBACK_DAYS: 14,
```

## Industry-Specific Configurations

### E-commerce
```javascript
const ECOMMERCE_CONFIG = {
  TARGET_TOP_OF_PAGE_IS: 0.75,        // High visibility for products
  BID_INCREASE_PERCENTAGE: 0.20,      // Aggressive for seasonal trends
  MIN_CONVERSION_RATE: 0.025,         // E-commerce typical rates
  MAX_BID_LIMIT: 15.00,               // Higher product margins
  LOOKBACK_DAYS: 7,                   // Weekly seasonality
};
```

### Lead Generation
```javascript
const LEADGEN_CONFIG = {
  TARGET_TOP_OF_PAGE_IS: 0.65,        // Moderate visibility
  BID_INCREASE_PERCENTAGE: 0.15,      // Standard increases
  MIN_CONVERSION_RATE: 0.015,         // Lower lead conversion rates
  MAX_BID_LIMIT: 25.00,               // High-value leads
  LOOKBACK_DAYS: 14,                  // Longer sales cycles
};
```

### Brand Protection
```javascript
const BRAND_CONFIG = {
  TARGET_TOP_OF_PAGE_IS: 0.90,        // Maximum brand visibility
  TARGET_ABSOLUTE_TOP_IS: 0.70,       // Dominate top position
  BID_INCREASE_PERCENTAGE: 0.25,      // Aggressive protection
  MAX_BID_LIMIT: 50.00,               // No limit for brand terms
  MIN_CONVERSION_RATE: 0.01,          // Lower threshold for brand
};
```

### SaaS/B2B
```javascript
const SAAS_CONFIG = {
  TARGET_TOP_OF_PAGE_IS: 0.70,        // Professional visibility
  BID_INCREASE_PERCENTAGE: 0.12,      // Conservative increases
  MIN_CONVERSION_RATE: 0.02,          // Trial/demo conversions
  MAX_BID_LIMIT: 30.00,               // High customer lifetime value
  LOOKBACK_DAYS: 14,                  // Longer consideration periods
};
```

## Advanced Configuration Patterns

### Campaign-Specific Settings
```javascript
// Check campaign name and apply different settings
function getCampaignConfig(campaignName) {
  if (campaignName.includes('brand')) {
    return BRAND_CONFIG;
  } else if (campaignName.includes('competitor')) {
    return COMPETITOR_CONFIG;
  } else {
    return DEFAULT_CONFIG;
  }
}
```

### Time-Based Configuration
```javascript
// Different settings for different times
function getTimeBasedConfig() {
  const hour = new Date().getHours();
  
  if (hour >= 9 && hour <= 17) {
    // Business hours - more aggressive
    return {
      ...CONFIG,
      BID_INCREASE_PERCENTAGE: 0.20,
      TARGET_TOP_OF_PAGE_IS: 0.80
    };
  } else {
    // Off hours - more conservative
    return {
      ...CONFIG,
      BID_INCREASE_PERCENTAGE: 0.10,
      TARGET_TOP_OF_PAGE_IS: 0.60
    };
  }
}
```

## Configuration Validation

### Automatic Validation
```javascript
function validateConfig(config) {
  const errors = [];
  
  if (config.TARGET_TOP_OF_PAGE_IS > 0.95) {
    errors.push('Target impression share too high (>95%)');
  }
  
  if (config.MAX_BID_LIMIT < config.MIN_BID_LIMIT) {
    errors.push('Max bid limit must be greater than min bid limit');
  }
  
  if (config.BID_INCREASE_PERCENTAGE > 0.50) {
    errors.push('Bid increase percentage too high (>50%)');
  }
  
  if (errors.length > 0) {
    throw new Error('Configuration errors: ' + errors.join(', '));
  }
}
```

## Best Practices

### 1. Start Conservative
Always begin with conservative settings and gradually increase aggressiveness

### 2. Monitor and Adjust
Review performance weekly and adjust thresholds based on results

### 3. Account for Seasonality
Adjust settings for holiday seasons and industry-specific cycles

### 4. Budget Alignment
Ensure configuration aligns with available budget constraints

---

## Configuration Troubleshooting

**Script timeouts:** Reduce `MAX_KEYWORDS_TO_ADJUST` and increase `BATCH_SIZE`  
**No bid changes:** Lower `MIN_IMPRESSIONS_THRESHOLD` and `MIN_CONVERSION_RATE`  
**Too aggressive bidding:** Reduce `BID_INCREASE_PERCENTAGE` and `MAX_BID_LIMIT`  
**Poor performance:** Increase `TARGET_TOP_OF_PAGE_IS` and review Quality Score factors
