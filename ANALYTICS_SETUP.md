# Vercel Web Analytics Setup Guide

This document explains how Vercel Web Analytics has been integrated into the Bulgariko project.

## Overview

Vercel Web Analytics is now enabled on this static HTML website to track visitor behavior and page views.

## What Was Done

### 1. Added Analytics Script to `index.html`

The Vercel Web Analytics script has been added to the `<head>` section of `index.html`:

```html
<!-- Vercel Web Analytics -->
<script>
    window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };
</script>
<script defer src="/_vercel/insights/script.js"></script>
```

This implementation:
- Initializes the `window.va` function for tracking events
- Defers loading the insights script to avoid blocking page rendering
- Works with plain HTML without requiring npm packages

## Prerequisites

To fully utilize Vercel Web Analytics, ensure:

1. **Vercel Account**: Sign up at [vercel.com/signup](https://vercel.com/signup) if you don't have one
2. **Vercel Project**: The repository should be connected to a Vercel project
3. **Deployment**: The site must be deployed to Vercel for analytics to work

## Enabling Web Analytics on Vercel

To enable Web Analytics for your Vercel project:

1. Go to [Vercel Dashboard](/dashboard)
2. Select your project (Bulgariko)
3. Click the **Analytics** tab
4. Click **Enable** in the dialog

> **Note**: Enabling Web Analytics will add new routes (scoped at `/_vercel/insights/*`) after your next deployment.

## Deployment

Deploy the app to Vercel using:

```bash
vercel deploy
```

Or connect your Git repository to enable automatic deployments:

```bash
# Connect your Git repository
vercel link

# Deploy on Git push
git push origin main
```

## Verification

After deployment, verify that analytics is working:

1. Visit your deployed site in a browser
2. Open Developer Tools (F12)
3. Go to the **Network** tab
4. Look for a request to `/_vercel/insights/view`
5. If you see this request, analytics is working correctly

## Viewing Analytics Data

Once your site is deployed and users have visited:

1. Go to [Vercel Dashboard](/dashboard)
2. Select your project
3. Click the **Analytics** tab
4. After a few days of visitors, you'll see analytics panels with data

## Features Available

- **Page Views**: Track which pages get the most traffic
- **Visitor Data**: Understand visitor patterns and behavior
- **Real-time Monitoring**: See live visitor activity

## Key Routes

The analytics script creates the following routes automatically:
- `/_vercel/insights/script.js` - The analytics tracking script
- `/_vercel/insights/view` - Where analytics data is sent

These routes are scoped and don't interfere with your application.

## Notes

- **No Node.js/npm required**: This implementation works with plain HTML
- **No route support**: The HTML implementation doesn't support framework-specific route tracking
- **Privacy**: Vercel Web Analytics follows privacy and compliance standards. See [Privacy Policy](https://docs.vercel.com/analytics/privacy-policy) for details

## Next Steps

For more information and advanced features, refer to:
- [Vercel Web Analytics Documentation](https://vercel.com/docs/analytics)
- [Custom Events Guide](https://vercel.com/docs/analytics/custom-events)
- [Data Filtering](https://vercel.com/docs/analytics/filtering)
- [Pricing and Limits](https://vercel.com/docs/analytics/limits-and-pricing)
- [Troubleshooting](https://vercel.com/docs/analytics/troubleshooting)

## Support

If you encounter any issues:
1. Check the troubleshooting guide
2. Ensure Vercel Web Analytics is enabled in the dashboard
3. Verify the site is deployed to Vercel (not localhost)
4. Check that the analytics script is loaded in the Network tab
