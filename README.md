# ClearVista CRM Widget - Quote Closed Won

A custom Zoho CRM widget that provides a confirmation dialog for marking quotes as "Closed Won" with stage-specific warnings.

## Features

- **Stage-Aware Prompts**: Shows different messages based on quote stage
- **Draft/Sent Warning**: Displays a warning when attempting to bypass Quote Ready and On Hold stages
- **Quote Information Display**: Shows quote ID, subject, and current stage
- **Success Confirmation**: Displays success message and creates sales order automatically
- **Responsive Design**: Works on desktop and mobile devices

## Widget Behavior

### For Draft or Sent Quotes
- **Warning Banner**: "THIS WILL BYPASS QUOTE READY AND ON HOLD STATUS"
- **Message**: "This will mark the quote as won and create a sales order"
- **Additional Info**: The quote will bypass the Quote Ready and On Hold stages and move directly to Closed Won status
- **Buttons**: "Accept, Proceed" or "Cancel"

### For On Hold or Quote Ready Quotes
- **No Warning Banner**: Direct transition is valid
- **Message**: "This will mark the quote as won and create a sales order"
- **Additional Info**: The quote will transition from [Current Stage] to Closed Won status
- **Buttons**: "Accept, Proceed" or "Cancel"

## Installation in Zoho CRM

1. **Setup Widget in Zoho CRM:**
   - Go to Setup → Customization → Buttons & Links
   - Find "Mark Closed Won" button or create a new button
   - Change the button action to "Widget"
   - Set the Widget to use this URL (once deployed):
     ```
     https://go-clear-vista.github.io/clearvista-crm-widget-quote-closed-won/
     ```
   - Set the button category to "View Layout"
   - Save the button

2. **Configure Button Properties:**
   - **Name**: Mark Closed Won
   - **Type**: Widget
   - **Widget URL**: https://go-clear-vista.github.io/clearvista-crm-widget-quote-closed-won/
   - **Profiles**: Select desired profiles (e.g., Sales, Operations)
   - **Layouts**: Select Quote layouts where the button should appear

3. **Workflow Setup:**
   - Ensure the "Quote is Closed Won" workflow rule is active
   - This will trigger the sales order creation and other downstream automations

## File Structure

```
clearvista-crm-widget-quote-closed-won/
├── index.html          # Main widget file
├── README.md          # This file
└── .gitignore         # Git ignore file
```

## API Requirements

This widget requires the following Zoho CRM API permissions:
- Read: Quotes module (to get quote details)
- Write: Quotes module (to update Quote_Stage field)

## Browser Compatibility

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Testing

### Test Mode
The widget includes a fallback testing mode when Zoho CRM Widget SDK is not available:
1. Open the HTML file directly in a browser
2. It will load with test data
3. Button interactions work normally (testing only)

### Production Testing
1. Deploy the widget to GitHub Pages
2. Configure it in Zoho CRM
3. Test by clicking the button on a quote record
4. Verify the stage information is displayed correctly
5. Test both Draft/Sent and Quote Ready/On Hold scenarios

## Deployment

### GitHub Pages Setup

1. **Enable GitHub Pages:**
   - Go to repository Settings
   - Scroll to "GitHub Pages"
   - Select "Deploy from a branch"
   - Choose "main" branch and "root" folder
   - Save

2. **Widget URL:**
   ```
   https://go-clear-vista.github.io/clearvista-crm-widget-quote-closed-won/
   ```

3. **Verify Deployment:**
   - Navigate to the URL above
   - You should see the widget interface

## Workflow Integration

When a quote is marked as Closed Won via this widget:

1. **Quote Stage Updated**: Quote_Stage field is changed to "Closed Won"
2. **Workflow Triggered**: "Quote is Closed Won" workflow rule executes
3. **Sales Order Created**: A sales order is automatically created in Zoho Books
4. **Deal Updated**: Related Deal record may be updated via "Update_Deal_from_Active_Quotes" workflow
5. **Record Locked**: Quote record is automatically locked (if configured)

## Troubleshooting

### Widget Not Loading
- **Issue**: Widget shows blank or doesn't load
- **Solution**: 
  - Check browser console for errors (F12)
  - Verify the GitHub Pages URL is correct
  - Ensure GitHub Pages is enabled in repository settings
  - Clear browser cache

### Quote Data Not Displaying
- **Issue**: Quote ID, subject, or stage shows "Loading..." or "N/A"
- **Solution**:
  - Verify Zoho CRM Widget SDK is loaded
  - Check that the quote record exists and is readable
  - Ensure user has read permission on Quotes module

### Update Not Working
- **Issue**: Clicking "Accept, Proceed" doesn't update the quote
- **Solution**:
  - Verify user has write permission on Quote_Stage field
  - Check browser console for API errors
  - Ensure quote record is not locked
  - Verify workflow rules are not blocking the update

### Workflow Rules Not Triggering
- **Issue**: Sales order not created after marking as Closed Won
- **Solution**:
  - Verify "Quote is Closed Won" workflow rule is active
  - Check workflow rule conditions and actions
  - Review workflow execution logs in Zoho CRM

## Support

For issues or questions:
1. Check the troubleshooting section above
2. Review Zoho CRM documentation on custom widgets
3. Check browser console for error messages
4. Contact ClearVista development team

## License

Internal use only - ClearVista employees

## Version

- **Version**: 1.0.0
- **Last Updated**: September 2026
- **Compatibility**: Zoho CRM (All Plans)
