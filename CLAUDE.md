# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **static documentation repository** for the Labcorp Diagnostic Assistant (DxA) customer onboarding process. The main deliverable is an interactive single-page HTML application (`index.html`) that visualizes the 8-phase onboarding workflow with multiple views, search functionality, and export capabilities.

**Note**: README.md refers to `onboarding-architecture-diagram.html`, but the actual file is `index.html`.

## Architecture

### Single-Page Application Structure

`index.html` is a self-contained ~3,300 line file with:
- **Styling**: Inline CSS + TailwindCSS (loaded via CDN) with Geist font family
- **Content**: Three complete view implementations (Current, Automated, Flowchart) embedded in HTML
- **Interactivity**: Vanilla JavaScript for all features (no frameworks)

### Three View Modes

The application renders different content based on active view:
1. **Current View** (`#current-view`) - Shows manual/existing process steps
2. **Automated View** (`#automated-view`) - Shows proposed automated workflow with implementation progress tracking
3. **Flowchart View** (`#flowchart-view`) - Visual flowchart with connected nodes

Views are toggled via `toggleView(view)` function which manages visibility and updates the UI state.

### 8-Phase Process Structure

Both Current and Automated views follow identical phase structure (Phase 0-7):
- **Phase 0**: Pre-Requisites
- **Phase 1**: Customer Information Receipt
- **Phase 2**: Pre-Creation Validation
- **Phase 3**: DocuSign Document Creation
- **Phase 4**: Pre-Send Automation Queue
- **Phase 5**: DocuSign Configuration & Sending
- **Phase 6**: Post-Signature Automation
- **Phase 7**: Pipeline/CRM Entry

Each phase contains multiple step cards with:
- Step type badges (Manual, Automated, Validation, API Call)
- Dependencies, API calls, tools, and level of effort metadata
- Color-coding matches legend (manual=orange, automated=green, validation=blue, api=pink)

### Client-Side Password Protection

**Login screen** added with password `dxa_1332` stored at line 3294:
```javascript
const correctPassword = 'dxa_1332';
```

**Security Note**: This is client-side only and not secure. Anyone can view source or DevTools to bypass. For true security, implement server-side authentication (e.g., Vercel serverless functions with environment variables).

Authentication state stored in `sessionStorage` under key `dxa-authenticated`.

### Key JavaScript Functions

- `togglePhase(header)` - Expand/collapse individual phase sections
- `toggleView(view)` - Switch between Current/Automated/Flowchart views
- `handleSearch()` - Search and highlight text across phases (line 2908)
- `expandAll()` / `collapseAll()` - Bulk phase controls
- `exportToPDF()` - Triggers browser print dialog
- `exportComparison()` - Generates CSV with ROI metrics
- `updateProgress()` - Calculates and displays implementation progress (Automated view only)
- `handleLogin(event)` - Validates password and shows/hides content (line 3286)

### Data Persistence

- **Progress tracking**: `localStorage.getItem('dxa-implementation-progress')` stores checkbox states for automated view
- **Authentication**: `sessionStorage.getItem('dxa-authenticated')` persists login during browser session

## Editing Guidelines

### Adding/Modifying Process Steps

Process content is duplicated across views. When adding steps:
1. Locate the phase in `#current-view` (starts ~line 1089)
2. Locate the same phase in `#automated-view` (starts ~line 1757)
3. Update both sections with consistent structure

Step card structure:
```html
<div class="step-card [type]">
    <div class="step-header">
        <div class="step-title">Title</div>
        <span class="badge [type]">Badge Text</span>
    </div>
    <div class="step-details">Description...</div>
    <!-- Optional sections: info-section, warning, success, etc. -->
</div>
```

Types: `manual`, `automated`, `validation`, `api-call`

### Sensitive Information

**Document editing password** at line 1332 has been redacted to `*****` (was previously an actual password).

When working with this file:
- Keep passwords redacted in HTML content display
- Store actual passwords in external secure locations
- Remember that anything in HTML source is visible to anyone

### Keyboard Shortcuts

Implemented keyboard navigation:
- `Escape` - Collapse all phases
- `Ctrl+E` - Expand all phases

## Deployment

This repository is deployed to **Vercel** as a static site. No build process required - Vercel serves `index.html` directly.

For true password protection on Vercel:
- **Option 1**: Upgrade to Vercel Pro for deployment-level password protection
- **Option 2**: Add serverless function (`/api/auth.js`) with environment variables for password validation

## File Structure

```
/
├── index.html                                   # Main interactive documentation
├── DxA Contracting Process - DocuSign for Automation.docx  # Detailed process doc
├── README.md                                    # Repository overview
├── index_html_summary.txt                       # Auto-generated summary
└── .gitignore                                   # macOS-specific ignores
```

## Testing Changes

1. Open `index.html` in browser (can use `open index.html` on macOS)
2. Test all three view toggles
3. Verify search functionality highlights correctly
4. Test expand/collapse behaviors
5. Check login screen (clear sessionStorage to reset: `sessionStorage.clear()` in DevTools)
6. Test export functions (PDF and CSV)
7. Validate on multiple browsers (Chrome, Firefox, Safari)

## External Dependencies

All dependencies loaded via CDN:
- **TailwindCSS**: `https://cdn.tailwindcss.com`
- **Google Fonts (Geist)**: `https://fonts.googleapis.com`

No `package.json`, no `npm install`, no build step required.
