# Agent Cards Plus for Genesys

A Chrome and Edge extension with clearer Genesys agent cards, saved contacts, shift notes, a sliding desk panel and click-to-call tools.

## Latest version: 1.3.4

[Download Agent-Cards-Plus-v1.3.4.zip](Agent-Cards-Plus-v1.3.4.zip?raw=true)

### Notes Backspace fix in 1.3.4

The sliding desk allowed editing keys to reach the website underneath. Because the page sees the drawer container instead of its hidden textarea, a page shortcut could cancel Backspace.

Keyboard, input, composition and clipboard events now stay inside the drawer without cancelling normal editing. The fix covers notes and contact fields, preserves form Escape handling, and leaves page shortcuts available outside the drawer. Deleting the final character remains saved even when an older save completes late.

Replace the files in the SAME installed folder, click **Reload** and refresh pages with the side tab. Saved notes are retained. This patch adds no permissions and includes the earlier calling fixes.

### Included calling fixes from 1.3.3

- Failed or stalled background checks no longer leave driver-number clicks permanently unresponsive. Disabled dispatch access shows a useful message.
- Confirmation supports telephone links and phone attributes on driver call controls, as well as the original iCabbi class. Conflicting numbers are rejected.
- Customer call popups are detected when populated late or reused for another number.
- An absolute deadline covers contact loading, site checks, dialler lookup and delivery. Expired requests cannot click Genesys later, and missing responses release the UI without automatic retries.
- Hidden old dialler controls no longer mask active controls. Disabled inputs and buttons, ambiguous diallers or a changed number prevent the call.
- Calling routes share duplicate protection for the selected Genesys tab. Dispatch results match the original request and document; uncertain delivery is reported honestly.
- UK numbers written as `+44 (0)...` are normalised consistently.

Reload the extension and refresh BOTH iCabbi and Genesys after updating. This version requires the updated Genesys receiver. No browser permissions are added.

### Included fixes from 1.3.2

- Older contact-save replies cannot hide new contacts or restore an outdated number on screen after another window edits them.
- Hiding or removing the side panel during startup stops its controllers and timers from loading afterwards.
- A delayed preferences read cannot undo the tab or theme you have just chosen in the side panel.
- The wallboard retains newer font size, theme and Auto fit changes received while it is loading.

Existing contacts migrate automatically, with save order retained across worker restarts. This update adds no browser permissions.

### Included fixes from 1.3.1

- Auto fit keeps working for widgets further down a scrolling dashboard, including full-width bands.
- Temporary card measurements preserve the table and page scroll position.
- Rapid preference changes stay in order during slow or failed saves. Older initial reads cannot undo a new edit, and “All saved” waits for completed writes.
- Handover copy and note export include the latest draft and tick-box choices. Older save replies cannot replace newer notes on screen.

Existing notes migrate automatically. That earlier patch added no browser permissions and did not change calling.

### Included from 1.3.0

- Brighter, full-card active-call pulses with reduced-motion support.
- Auto fit chooses card size and columns for each Agent Status widget and reserves dashboard space in full-width mode.
- A separate 75% to 200% text-size control. Cards grow and columns adjust to accommodate larger names, statuses and timers.
- Saved manual sizes remain available when Auto fit is switched off.

Contacts, notes, the sliding desk, right-click calling and the earlier call-popup fixes are included.

## Update an existing installation

1. Download and extract the latest ZIP.
2. Copy the contents of `Agent-Cards-Plus` into the folder your existing extension is loaded from, replacing the old files.
3. Open `chrome://extensions` or `edge://extensions` and click **Reload**.
4. Refresh your Google, Genesys and dispatch tabs.
5. For a large wallboard, choose **Appearance > Big screen**. Use **Card layout > Text size only** to adjust the writing independently.

Updating the same extension folder retains its identity and saved data. Avoid uninstalling it or loading a different folder as a second copy when updating.

## If iCabbi still shows no confirmation

Check that its exact hostname is enabled under **Sites**, then refresh iCabbi. The top-level dispatch handler recognises the original `.init-call` control and `tel:` links. If a different control is used or dispatch is embedded in a frame, provide the clicked element's HTML from Inspect with the real number replaced by an example. The separate **Call through Genesys** right-click action remains available for highlighted numbers.

## First installation

Extract the ZIP, enable **Developer mode** on the browser's Extensions page, and choose **Load unpacked**. Select the extracted `Agent-Cards-Plus` folder containing `manifest.json`. Enable your exact Genesys and dispatch sites from the extension's **Sites** tab, then refresh them.

The archive includes the source code, full README, installation guide and tests. Run `node --test` from the extracted extension folder with Node 18 or newer.

## Validation

All 199 automated checks passed for v1.3.4. Five new checks cover the Backspace/page-shortcut conflict, saved deletions, editing and clipboard events, outside-page shortcuts, form Escape handling and clearing a note during delayed saves. Three failing event-propagation checks were reproduced before the fix. JavaScript syntax, asset references and ZIP integrity also passed.

These checks use simulated documents, event propagation, editing defaults, geometry, clocks and browser APIs. Native browser keyboard input was not verified. The reported live iCabbi page was unavailable for inspection, so its current markup and the exact cause of the incident have not been verified. No real phone call was made. Live iCabbi/Genesys integration still needs checking after installation.

Auto fit targets Agent Status widgets. Other native Genesys widgets retain their own content layout and scrolling.
