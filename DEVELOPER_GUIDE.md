# 🛠️ Developer Guide - Sar-E-Darya Dashboard

This guide provides technical details for developers to maintain and modify the Sar-E-Darya Restaurant Management Dashboard.

## 🏗️ Architecture
The application is a **Single-file HTML Application** (Self-contained). It does not require a backend server or database; all logic is executed in the browser.

### 🏗️ Technology Stack
- **Frontend**: HTML5, CSS3, JavaScript (ES6+).
- **Libraries**:
  - `ExcelJS` (via CDN): Used for generating complex Excel files with formatting.
  - `Google Fonts`: Playfair Display & DM Sans.

## 📁 Key Components

### 1. CSS Custom Properties (Theming)
The "Khajoor" theme is controlled via CSS variables in the `:root` section.
```css
:root {
  --khajoor: #5D4037; /* The signature brown */
  --palm: #2E7D32;    /* The leaf green */
  --sand: #C5A059;    /* The sand/gold highlight */
}
```

### 2. Data Persistence (`localStorage`)
The app saves data in the browser's local storage using the `srd_` prefix.
- **Key Format**: `srd_YYYY-MM-DD` (e.g., `srd_2026-05-15`).
- **Data Structure**: A JSON object containing arrays for `stock`, `expenses`, `wages`, and objects for `notes` and `directSale`.

### 3. Core Functions
- `calcAll()`: The main engine that calculates all totals and net profit. It is triggered on every input change.
- `autoSave()`: Silently saves the current state to `localStorage` whenever a change is detected.
- `loadDate(date)`: Clears the current UI and populates it with data from the specified date.
- `exportExcel()`: Logic for generating the premium A4 report.

## 🛠️ How to Edit

### Changing Colors
Simply update the hex codes in the `:root` section at the top of the `<style>` tag.

### Adding Expense Types or Categories
Modify the constants at the beginning of the script:
```javascript
const ETYPES = ['سیلری/Salary', 'کرایہ/Rent', ...];
const STCATS = ['گوشت/Meat', 'مرغی/Chicken', ...];
```

### Modifying Excel Layout
The Excel generation logic is inside `exportExcel()`. You can adjust column widths, colors, and headers using the `ExcelJS` API.

## 🚀 Deployment
Since it's a single file, you can host it on:
- **GitHub Pages**: Just upload the file and name it `index.html`.
- **Local Server**: Any local HTTP server (e.g., `live-server` in VS Code).
- **Offline**: Simply open the file directly in a browser.

---
*Developed by Antigravity AI*
