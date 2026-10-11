# Agent Cards Plus for Genesys

A Chrome and Edge extension with clearer Genesys agent cards, saved contacts, shift notes, a sliding desk panel and click-to-call tools.

## Latest version: 1.3.2

[Download Agent-Cards-Plus-v1.3.2.zip](Agent-Cards-Plus-v1.3.2.zip?raw=true)

### Bug fixes in 1.3.2

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

Existing notes migrate automatically. This patch adds no browser permissions and does not change the calling logic.

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

## First installation

Extract the ZIP, enable **Developer mode** on the browser's Extensions page, and choose **Load unpacked**. Select the extracted `Agent-Cards-Plus` folder containing `manifest.json`. Enable your exact Genesys and dispatch sites from the extension's **Sites** tab, then refresh them.

The archive includes the source code, full README, installation guide and tests. Run `node --test` from the extracted extension folder with Node 18 or newer.

## Validation

All 156 automated checks passed for v1.3.2, including nine new checks for delayed contact replies, interrupted panel startup, preference restoration, migration and storage failures. Checks use simulated documents, geometry and browser APIs. The current layout and real account integration still need checking on a live Genesys wallboard; no real phone call was made during testing.

Auto fit targets Agent Status widgets. Other native Genesys widgets retain their own content layout and scrolling.
