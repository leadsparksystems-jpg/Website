# Multi-Step Form Engine — Handoff

## What this is

A universal multi-step form engine for Webflow. One JS script handles step navigation, conditional branching, radio auto-advance, and back-with-clear. Only the CONFIG section at the top changes per form.

---

## Architecture

- **Form UI:** Built in Webflow Designer using native form elements
- **JavaScript:** One script in a Webflow code embed block
- **Step visibility:** JS uses `display: none` / `display: flex` to show/hide steps
- **Conditional logic:** JS reads `data-branch` attributes and a config object to determine which steps are in the active sequence
- **Height:** JS measures the tallest step on load and sets `min-height` on the wrapper. Recalculates on window resize.
- **Webflow layout:** Keep the original grid/flexbox layout set in the Webflow Designer on the form wrapper and step divs. The engine only controls `display` on step divs — do not override the wrapper's layout in Webflow. Step divs should be set to Flexbox column with justify space-between so buttons pin to the bottom.

---

## File

`multistep-form-engine.html` — paste the full contents into a Webflow code embed block inside the form wrapper, after the last step div.

---

## Webflow structure

```
<div id="qf-general">              ← direct parent of all steps
  <div data-step="1">              ← step 1
  <div data-step="2">              ← step 2
  ...
  <div data-step="10">             ← step 10
  <!-- CODE EMBED WITH SCRIPT -->
</div>
```

All step divs must be **direct children** of the `qf-general` wrapper.

---

## Step map (Arctic Wellness form)

| Step | Content | Type | Condition |
|------|---------|------|-----------|
| 1 | Set Up Type (Commercial / Residential) | auto-advance | always |
| 2 | Build Type (Sauna / Ice Bath / Both) | auto-advance | always |
| 3 | Sauna Type (Custom / Pre-Built) | auto-advance | `data-branch="sauna"` |
| 4 | Custom Sauna Details (1) | next/skip/add-another | `data-branch="sauna,custom"` |
| 5 | Custom Sauna Details (2) | next/skip/add-another | `data-branch="sauna,custom"` |
| 6 | Custom Sauna Details (3) + "for more get in touch" | next/skip | `data-branch="sauna,custom"` |
| 7 | Pre-Built Sauna (model + qty) | next | `data-branch="sauna,prebuilt"` |
| 8 | Outdoor Shower upsell (Yes / No) | auto-advance | `data-branch="sauna"` |
| 9 | Ice Bath Type | auto-advance | `data-branch="icebath"` |
| 10 | Ice Bath Quantity | next | `data-branch="icebath"` |

---

## Custom attributes reference

### On step divs

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `data-step` | Step number (required on every step) | `data-step="1"` |
| `data-branch` | Conditional visibility. Comma-separated = AND logic | `data-branch="sauna,custom"` |

### On radio buttons (inputs)

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `data-branch-trigger` | Names the trigger group (matches branchRules key) | `data-branch-trigger="build-type"` |
| `data-qf-next` | Auto-advance on selection | `data-qf-next="true"` |

### On buttons

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `data-qf-next` | Go to next step in active sequence | `data-qf-next="true"` |
| `data-qf-back` | Go back one step, clear the step being left | `data-qf-back="true"` |
| `data-qf-skip` | Jump to a specific step number | `data-qf-skip="8"` |
| `data-qf-add-another` | Go to next step (same as data-qf-next) | `data-qf-add-another="true"` |

### On conditional fields within a step

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `data-show-if` | Show element only when a field has a specific value | `data-show-if="setup-type:commercial"` |

---

## Radio button setup in Webflow

Each radio button needs:

1. **Group Name** — this becomes the HTML `name` attribute. Must match what `data-branch-trigger` and `data-show-if` reference. Use hyphens, no spaces. Examples: `setup-type`, `build-type`, `sauna-type`
2. **Choice Value** — the value sent when selected. Must match the branchRules config exactly. Lowercase, no spaces. Examples: `sauna`, `icebath`, `both`, `custom`, `prebuilt`, `commercial`, `residential`
3. **Custom attributes** — `data-branch-trigger` and optionally `data-qf-next`

---

## CONFIG section (what changes per form)

```javascript
var CONFIG = {
  formId: 'qf-general',      // ID of the wrapper div

  branchRules: {
    'build-type': {           // trigger name (matches data-branch-trigger)
      'sauna':   ['sauna'],   // value → branches to activate
      'icebath': ['icebath'],
      'both':    ['sauna', 'icebath']
    },
    'sauna-type': {
      'custom':   ['custom'],
      'prebuilt': ['prebuilt']
    }
  },

  autoAdvanceDelay: 300,      // ms delay before auto-advance on radio select

  onComplete: function (formData) {
    // Hook for quote engine — receives all form data as object
    console.log('Form complete:', formData);
  }
};
```

---

## How branching works

1. User selects a radio with `data-branch-trigger="build-type"` and `value="sauna"`
2. Engine looks up `branchRules['build-type']['sauna']` → `['sauna']`
3. Engine activates the `sauna` branch
4. Steps with `data-branch="sauna"` enter the active sequence
5. Steps with `data-branch="sauna,custom"` need BOTH `sauna` AND `custom` active
6. `custom` gets activated when the user selects custom on step 3 (`data-branch-trigger="sauna-type"`)

---

## How back works

1. Clears all fields on the step being left (radios unchecked, dropdowns reset, text cleared)
2. Removes Webflow's visual radio styling (`w--redirected-checked` class)
3. Clears any branch triggers on the leaving step (deactivates downstream branches)
4. Cascades: if branch A deactivated, any triggers inside branch A's steps are also cleared
5. Returns to the previous step in history

---

## How data-show-if works

`data-show-if="setup-type:commercial"` means:
- Look for a radio with `name="setup-type"` that is `:checked`
- If its value is `commercial`, show this element
- Otherwise hide it (display: none)

Supports multiple values: `data-show-if="setup-type:commercial,enterprise"`

---

## How data-qf-skip works

`data-qf-skip="8"` means:
- On click, jump directly to the step with `data-step="8"`
- The current step is added to back history
- The target step doesn't need to be in the active branch sequence

Use case: "Next" buttons on steps 4/5/6 skip past the remaining custom sauna steps to step 8 (outdoor shower).

---

## Cloning to a new project

1. Copy the `multistep-form-engine.html` script
2. Build form steps in Webflow following the attribute conventions above
3. Change only the CONFIG section:
   - `formId` → your wrapper's ID
   - `branchRules` → your trigger-to-branch mapping
   - `onComplete` → your submission/quote logic
4. Paste the script into a code embed inside the wrapper

---

## How to extend (adding steps / branches)

### Adding a plain step (always shows)

**Webflow only — no code changes:**

1. Add a step div inside `#qf-general` with `data-step="N"` (next number in sequence)
2. Add buttons: `data-qf-next="true"` to advance, `data-qf-back="true"` to go back
3. Done — the engine picks it up automatically by `data-step` order

The step number controls **ordering** only. Keep it sequential for sanity.

### Adding a conditional step (shows only for certain answers)

**Webflow:**

1. Add the step div with `data-step="N"` **and** `data-branch="branchname"`
2. For AND logic, comma-separate: `data-branch="sauna,custom"` (needs BOTH active)

**Code (`CONFIG.branchRules`)** — only if a *new answer* activates it:

```javascript
branchRules: {
  'build-type': {        // ← radio's data-branch-trigger (Group Name)
    'sauna':   ['sauna'],   // ← Choice Value → branch name(s) to activate
    'icebath': ['icebath'],
    'both':    ['sauna', 'icebath']
  }
}
```

- **Left key** = the radio's `data-branch-trigger` attribute (its Group Name)
- **Middle key** = the radio's Choice Value
- **Right array** = branch name(s) to activate → must match `data-branch` on the step divs

Reusing an existing branch (another `data-branch="sauna"` step)? **No code change** — just the Webflow attribute.

### Adding a whole new branch (new question → new path)

Example: a "Lighting" question that opens lighting steps.

1. **Webflow:** radio group with `data-branch-trigger="lighting-type"`, choice values `led`/`none`, plus `data-qf-next="true"` if it auto-advances
2. **Webflow:** the new steps get `data-branch="led"`
3. **Code:** add to `branchRules`:

```javascript
'lighting-type': {
  'led':  ['led'],
  'none': []
}
```

### Quick reference — attributes that matter

| Want | Attribute (in Webflow) |
|------|------------------------|
| A step | `data-step="N"` on the div |
| Show step conditionally | `data-branch="x"` (or `"x,y"` for AND) |
| Radio that opens a branch | `data-branch-trigger="groupname"` |
| Radio that auto-advances | `data-qf-next="true"` |
| Next button | `data-qf-next="true"` |
| Back button | `data-qf-back="true"` |
| Skip to a specific step | `data-qf-skip="8"` |
| "Add another" repeatable step | `data-qf-add-another="true"` + `data-add-step` on the step |

### The one rule that trips people up

**Choice Values and branch names must match exactly** — lowercase, no spaces — across three places: the radio's Choice Value in Webflow, the middle key in `branchRules`, and the `data-branch` on the step. One typo and the step silently won't appear.

---

## Known constraints

- All step divs must be direct children of the wrapper (the engine moves them with `appendChild` on init)
- Radio Group Names must use hyphens, no spaces (engine uses them in CSS selectors)
- Choice Values must be lowercase with no spaces
- `data-show-if` references the radio Group Name, not the data-branch-trigger
- The engine prevents default Webflow form submission — handle submission in `onComplete`
- Dropdown placeholder text requires explicit text color in Webflow (not inherited)

---

## Quote engine integration (future)

The `onComplete` callback receives all form data as a key-value object:

```javascript
{
  'setup-type': 'commercial',
  'build-type': 'sauna',
  'sauna-type': 'custom',
  'sauna-size-1': '4x6',
  'sauna-wood-1': 'cedar',
  'sauna-heating-1': 'electric',
  'outdoor-shower': 'yes',
  ...
}
```

The quote engine will plug into this callback to calculate and display the price.

---

## Webflow element IDs to confirm

| Element | ID |
|---------|-----|
| Form wrapper (direct parent of steps) | `qf-general` |

All other targeting uses `data-step`, `data-branch`, and `data-*` custom attributes — no other IDs required.
