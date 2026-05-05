# Installation Guide

Complete step-by-step guide to install any vertical in Cognigy.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Step-by-Step Installation](#step-by-step-installation)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)
- [Next Steps](#next-steps)

---

## Prerequisites

### Required
- Cognigy account
- Admin or packaging permissions
- Downloaded `.zip` package file
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Recommended
- 100 MB free disk space
- Stable internet connection
- Microphone (for voice testing)
- 30 minutes for first installation

---

## Getting Started

### Step 1: Download Package

1. Go to [Verticals Index](../verticals/VERTICALS-INDEX.md)
2. Select your vertical
3. Open vertical README
4. Click "Download Latest Package"
5. Save to easily accessible location (Desktop/Downloads)

**File format:** `vertical-name-language-v1.0.zip`

### Step 2: Prepare Cognigy

1. Open Cognigy dashboard
2. Log in with your credentials
3. Navigate to **Settings** → **Packages**
4. Verify "Import" button is visible

---

## Step-by-Step Installation

### Step 1: Access Packaging

**In Cognigy Dashboard:**
1. Click **Settings** (gear icon, bottom-left)
2. Scroll to **Packages** section
3. Click **Packages**

You should see a list of installed packages.

### Step 2: Import Package

1. Click **Import Package** button (blue button)
2. Dialog opens: "Select Package File"
3. Choose method:
   - **Drag & Drop:** Drag `.zip` into the box
   - **Click to Browse:** Click and select file

**Example:**
one-seguro-pt-br-v1.0.zip ✓ Selected

### Step 3: Wait for Upload

Progress bar appears. This may take 1-2 minutes depending on:
- File size
- Internet speed
- Cognigy server load

**Status messages:**
- "Uploading..." → File being transferred
- "Processing..." → System analyzing package
- "Ready to Import" → File validated, ready

### Step 4: Review Package Contents
Review and confirm everything looks correct.

### Step 5: Click Import Button

Large blue **IMPORT** button appears at bottom-right.

Click it to complete import.

### Step 6: Wait for Confirmation

System processes the import:
- Creates flows
- Sets up integrations
- Configures settings
- Validates everything

**Success message appears:**
✅ Package imported successfully!
the flows are added to your agent.
You can now start using them.

### Step 7: Assign to Agent

Flows are now available, but need to be assigned to an agent:

1. In Cognigy, go to **Agents**
2. Click the agent where you want the flow
3. In **Settings**, select **Flows**
4. Click **Add Flow**
5. Select the newly imported flow
6. Click **Save**

---

## Verification

### Check Installation

**In Cognigy:**

1. **Flows List** → Should see new flows
✓ One Seguro - Welcome
✓ One Seguro - Claim Voice
✓ One Seguro - Claim Web

2. **Agent Assignment** → Flow attached to agent
Agent: "Sarah"
Flows: [One Seguro - Welcome] ✓

3. **No Errors** → Red error indicators absent
Configuration: ✓ Valid
Integrations: ✓ Connected
Scripts: ✓ No errors

### Test the Flow

1. **Open Preview**
   - Click agent name
   - Click **Preview** button
   - Chat window opens

2. **Test greeting**
   - You see: Agent welcome message
   - Say/Type: "Hello"
   - Agent responds naturally

3. **Test main flow**
   - Say/Type: "I want to report a claim"
   - Agent: Asks follow-up questions
   - Flow working ✓

---

## Language Variations

If importing multiple languages:

**Install each separately:**

1. Import `one-seguro-pt-br-v1.0.zip`
2. Then import `one-seguro-es-v1.0.zip`

**Or create language selector:**

1. Import all three
2. Create wrapper flow that asks language
3. Routes to correct language flow

---

## Customization (Optional)

After importing, you can customize:

### Change Company Name
1. Find script nodes
2. Update `DEFAULT_COMPANY` variable *The XApps wont change based on this*
3. Save and test

---

## Troubleshooting

### Issue: "File is too large"

**Solution:**
- Maximum file size: 100 MB
- Your file: Check size
- Download fresh copy
- Try different browser
- Contact support if persists

### Issue: "Import button not appearing"

**Solution:**
- Verify admin permissions
- Check browser cookies enabled
- Clear cache: Ctrl+Shift+Delete
- Try different browser
- Refresh page: F5

### Issue: "Upload completes but no success message"

**Solution:**
- Wait 30 seconds (processing)
- Refresh page: F5
- Check Flows list manually
- Check browser console for errors
- Try again with fresh download

### Issue: "Flow appears but won't open"

**Solution:**
- Assign to agent first
- Reload Cognigy dashboard
- Check for dependency issues
- Review error messages
- Contact support

### Issue: "Conversations don't work"

**Solution:**
- Test in Preview mode first
- Check integrations connected
- Verify all dependencies
- Review flow error logs
- Check conversation example in docs

---

## Post-Installation Checklist

- [ ] File downloaded successfully
- [ ] Import process completed
- [ ] No error messages
- [ ] Flows visible in Cognigy
- [ ] Flow assigned to agent
- [ ] Preview mode works
- [ ] Welcome message displays
- [ ] Can interact with agent
- [ ] Language correct (if applicable)
- [ ] Ready for demo

---

## Next Steps

After successful installation:

1. **Review Documentation**
   - Read vertical README
   - Review conversation flows
   - Check demo script

2. **Prepare for Demo**
   - Follow demo script
   - Practice conversation flows
   - Prepare talking points

3. **Customize (if needed)**
   - Adjust settings
   - Add integrations
   - Modify language

4. **Run Demo**
   - Test with preview
   - Present to audience
   - Gather feedback

---

## Need Help?

- **Installation Issues** → [Troubleshooting](#troubleshooting)
- **Understanding Flows** → See vertical README
- **Demo Questions** → See demo script
- **Cognigy Help** → https://docs.cognigy.com
- **Report Bugs** → Create GitHub issue

---

**Estimated Time:** 15-30 minutes  
**Version:** 1.0  
**Last Updated:** May 4, 2025