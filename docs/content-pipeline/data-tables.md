# Data Tables

**Overlooted → Content → Data Tables**

A tabbed spreadsheet view of every JSON registry. Sort, filter, edit inline, delete rows, or launch the wizard to add a new one — all without touching a JSON file directly.

## Overview

<div style="background:#282828;border:1px solid #111;border-radius:4px;padding:0;font-family:'Segoe UI',sans-serif;font-size:12px;color:#c8c8c8;max-width:860px;overflow:hidden;margin:16px 0;">

  <!-- Tab bar -->
  <div style="display:flex;background:#232323;border-bottom:1px solid #111;">
    <div style="padding:6px 14px;background:#282828;border-right:1px solid #111;border-bottom:2px solid #4a90d9;color:#fff;font-weight:bold;">Items</div>
    <div style="padding:6px 14px;color:#888;border-right:1px solid #111;">Tools</div>
    <div style="padding:6px 14px;color:#888;border-right:1px solid #111;">Zones</div>
    <div style="padding:6px 14px;color:#888;border-right:1px solid #111;">Vendors</div>
    <div style="padding:6px 14px;color:#888;border-right:1px solid #111;">Rarities</div>
    <div style="padding:6px 14px;color:#888;">Upgrades</div>
  </div>

  <!-- Toolbar -->
  <div style="display:flex;align-items:center;background:#2a2a2a;border-bottom:1px solid #111;padding:4px 8px;gap:6px;">
    <span style="color:#888;font-size:11px;">Filter:</span>
    <div style="background:#1e1e1e;border:1px solid #111;padding:2px 8px;width:160px;color:#c8c8c8;font-size:11px;">sword</div>
    <span style="color:#555;cursor:pointer;">✕</span>
    <span style="color:#666;font-size:11px;margin-left:4px;">2 / 8 rows</span>
    <div style="flex:1;"></div>
    <div style="background:#3a3a3a;border:1px solid #222;padding:3px 10px;font-size:11px;color:#c8c8c8;cursor:pointer;">New Items…</div>
    <div style="background:#3a3a3a;border:1px solid #222;padding:3px 10px;font-size:11px;color:#c8c8c8;cursor:pointer;">Save</div>
  </div>

  <!-- Column headers -->
  <div style="display:flex;background:#333;border-bottom:1px solid #111;font-size:11px;font-weight:bold;color:#aaa;">
    <div style="width:150px;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">ID ▲</div>
    <div style="width:120px;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">Display Key</div>
    <div style="width:80px;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">Type</div>
    <div style="width:110px;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">Rarity</div>
    <div style="width:60px;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">Value</div>
    <div style="width:60px;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">Weight</div>
    <div style="width:110px;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">Mesh ID</div>
    <div style="flex:1;padding:3px 6px;border-right:1px solid #222;cursor:pointer;">Vendor Tags</div>
    <div style="width:28px;padding:3px 4px;"></div>
  </div>

  <!-- Row 1 (even) -->
  <div style="display:flex;background:#2e2e2e;border-bottom:1px solid #222;align-items:center;font-size:11px;">
    <div style="width:150px;padding:2px 6px;border-right:1px solid #222;color:#aaa;">item.bronze_sword</div>
    <div style="width:120px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">item.bronze_sword</div></div>
    <div style="width:80px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">Weapon ▾</div></div>
    <div style="width:110px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#2d4a2d;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">rarity.common</div></div>
    <div style="width:60px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">45</div></div>
    <div style="width:60px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">1</div></div>
    <div style="width:110px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">bronze_sword</div></div>
    <div style="flex:1;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">general, weapons</div></div>
    <div style="width:28px;padding:2px 4px;color:#c04040;cursor:pointer;text-align:center;">✕</div>
  </div>

  <!-- Row 2 (odd) - amber validation on rarity -->
  <div style="display:flex;background:#323232;border-bottom:1px solid #222;align-items:center;font-size:11px;">
    <div style="width:150px;padding:2px 6px;border-right:1px solid #222;color:#aaa;">item.runed_sword</div>
    <div style="width:120px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">item.runed_sword</div></div>
    <div style="width:80px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">Weapon ▾</div></div>
    <div style="width:110px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#4a3a10;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">rarity.runed</div></div>
    <div style="width:60px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">280</div></div>
    <div style="width:60px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">1</div></div>
    <div style="width:110px;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">runed_sword</div></div>
    <div style="flex:1;padding:2px 4px;border-right:1px solid #222;"><div style="background:#1e1e1e;border:1px solid #111;padding:1px 4px;color:#c8c8c8;">general, weapons</div></div>
    <div style="width:28px;padding:2px 4px;color:#c04040;cursor:pointer;text-align:center;">✕</div>
  </div>

  <!-- Footer hint -->
  <div style="padding:4px 8px;font-size:10px;color:#555;border-top:1px solid #1a1a1a;background:#252525;">
    Green rarity field = valid reference &nbsp;|&nbsp; <span style="color:#7a5a10;">■</span> Amber = ID not found in rarities.json &nbsp;|&nbsp; Click any column header to sort
  </div>

</div>

## Features

### Sorting

Click any column header to sort by that column. Click again to reverse. A ▲ or ▼ indicator shows the active sort direction. Numbers sort numerically — `100` sorts before `90` correctly.

### Filtering

The filter box searches across all text fields in every row. Typing `sword` in Items shows only rows where any field contains "sword". The row count updates to show `2 / 8 rows`.

### Inline Validation

Reference fields (like Rarity on items) are colour-coded:

| Colour | Meaning |
|---|---|
| Green background | ID exists in the referenced registry |
| Amber background | ID not found — will be flagged by the data validator |
| Plain | Empty or non-reference field |

The Console data validator also runs immediately after saving, so broken references are caught twice.

### Editing

Most fields are editable directly in the table. Arrays (like Vendor Tags, Unlocks Zones) are shown as comma-separated text — edit as `general, weapons` and it saves back as a JSON array.

| Column type | Behaviour |
|---|---|
| ID | Read-only — generated by wizards, changing breaks references |
| Text | Editable text field |
| Int / Float | Numeric field |
| Enum | Dropdown (e.g. Item Type) |
| Color | Color picker — saves as hex `#RRGGBB` |
| Comma-separated | Edit as `a, b, c` → saves as `["a","b","c"]` |
| `[N items]` | Complex nested array — edit via wizard |

### Adding Rows

**New Items…** in the toolbar opens the New Item Wizard. After the wizard creates the entry, switch back to Data Tables and the new row appears.

### Deleting Rows

Click ✕ on any row to delete it immediately. No confirmation. The data validator will surface any broken references in the Console straight away.

### Saving

The **Save** button turns yellow when there are unsaved changes. Switching tabs or closing the window auto-saves. The file is written as formatted JSON and Unity reimports it automatically.
