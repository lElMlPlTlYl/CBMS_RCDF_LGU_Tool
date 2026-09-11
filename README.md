# CBMS RCDF LGU Tool

**Community-Based Monitoring System (CBMS) — RCDF Desktop Application for Local Government Units (LGUs)**

A standalone Windows desktop application that enables municipalities to import, visualize, analyze, and export CBMS 2024 census data from official PSA-distributed RCDF (Regional Census Data Format) files — with zero setup required.

---

## Overview

The CBMS RCDF LGU Tool is a self-contained desktop application built for Philippine Local Government Units (LGUs) to manage and analyze their CBMS 2024 census data. It reads encrypted RCDF files distributed by the Philippine Statistics Authority (PSA), decrypts and imports the data automatically, and provides a rich dashboard for exploring household, person, and barangay-level statistics.

### Key Features

- **One-click RCDF Import** — Upload your PSA-distributed RCDF file, enter the passphrase, and the app handles decryption, conversion, and database insertion automatically. No command-line tools, no Python, no technical expertise required.
- **Three-Module Analytics**:
  - **Person Module** — Browse 56,000+ person records with demographics, education, employment, health, disability, and migration data (Sections A–E)
  - **Household Module** — Explore 15,000+ household records with food security, health, water & sanitation, housing, financial inclusion, disasters, and social protection data (Sections F–O)
  - **Barangay Module** — View barangay-level DRRM readiness, infrastructure, agriculture, and food security indicators
- **Advanced Filtering** — Multi-select filters across all CBMS sections with real-time pie chart visualizations
- **Excel Export** — Export filtered data to Excel with all coded fields automatically decoded to human-readable labels
- **Statistical Tables** — Create, save, and export custom statistical tables with cross-tabulation support
- **Machine-Locked Licensing** — Each installation is bound to a specific computer via a cryptographic machine fingerprint. Licenses are signed with RSA-2048 and verified offline — no internet connection required after activation.
- **14-Day Free Trial** — Try all features free for 14 days before activating a license
- **Data Reset** — Super admin can wipe all data and re-import fresh RCDF data at any time
- **Multi-Municipality Support** — Import and switch between multiple municipalities (for consolidator use cases)
- **Auto-Logout Security** — Automatic session timeout after 1 hour of inactivity
- **No Internet Required** — The app runs entirely offline after installation

### System Requirements

| Requirement | Minimum |
|-------------|---------|
| OS | Windows 10 64-bit or later |
| RAM | 4 GB (8 GB recommended) |
| Disk Space | 2 GB free |
| Internet | Only needed for download and license activation communication with provider |

### Tech Stack

- **Backend:** PHP 8.3, Laravel 13
- **Frontend:** Vue 3, Inertia.js, Vite, TailwindCSS
- **Database:** SQLite (embedded, no server needed)
- **Desktop Shell:** Electron (via NativePHP)
- **Bundled Runtime:** PHP 8.3, Python 3.12 (for RCDF decryption), SQLite
- **Charts:** Chart.js
- **Excel Export:** PhpSpreadsheet

---

## Installation

### Step 1 — Download

Download the latest installer from the [Releases page](../../releases):

- **`CBMS-1.0.0-setup.exe`** (~918 MB) — NSIS installer with desktop shortcut

### Step 2 — Run the Installer

1. Double-click `CBMS-1.0.0-setup.exe`
2. Follow the installation wizard (click Next → Install → Finish)
3. A desktop shortcut labeled **CBMS** will be created

### Step 3 — First Launch

1. Double-click the **CBMS** desktop shortcut
2. The app will open in a desktop window and auto-initialize its database
3. You will see the **login screen**

### Default Login

| Field | Value |
|-------|-------|
| Email | `superadmin@gmail.com` |
| Password | `superadmin` |

> **IMPORTANT:** Change the default password immediately after first login via Profile → Update Password.

---

## Initial Setup Guide

### 1. Activate Your License or Start a Trial

On first launch, you'll be prompted to activate a license or start a free trial.

**Option A — Start a 14-Day Free Trial:**
1. Click **"Start 14-Day Free Trial"**
2. You'll have full access to all features for 14 days
3. After the trial, you'll need to activate a license to continue

**Option B — Activate a License:**

The licensing system uses a two-step activation process:

1. **Send your Machine Key** — On the activation screen, copy your unique Machine Key (a 64-character hex string) and send it to the contact below
2. **Receive your License Key** — We'll generate a license key bound to your specific computer and send it back
3. **Enter your License Key** — Paste the license key into the activation screen and click "Activate"

You can send your Machine Key via:
- **Email:** kyuubi.raganit.rtzverka2@gmail.com
- **Phone:** 0962 409 8673 / 0995 892 4433

> The Machine Key can be copied from the activation screen or scanned via the QR code displayed on-screen.

### 2. Import Your RCDF Data

Once logged in:

1. Click **Admin** → **Data Management** in the sidebar
2. In the **"Import RCDF File"** section:
   - Click **Browse** and select your `.rcdf` file (distributed by PSA)
   - Click **Browse** and select your private key `.pem` file
   - Enter the **private key passphrase** (provided by PSA)
   - Select your **municipality** from the dropdown
3. Click **"Start Import"**
4. Wait for the import to complete (typically 2–5 minutes depending on data size)
5. You'll see a summary of imported records (households, residents, barangay records)

> The app handles decryption, Parquet conversion, and database insertion automatically using its bundled Python runtime. No external tools needed.

### 3. Explore Your Data

After import, navigate using the sidebar:

- **Dashboard** — Overview statistics (total households, residents, seniors, PWDs, food insecurity, etc.)
- **Person Module** — Browse and filter individual person records
- **Household Module** — Browse and filter household records with all section data
- **Barangay Module** — View barangay-level DRRM, infrastructure, and agriculture data
- **Statistical Tables** — Create custom tables and export to Excel
- **Activity Logs** — Audit trail of all actions (imports, exports, user changes, etc.)

### 4. Export Data

- Use the **Advanced Filter Panel** on any module page to filter records
- Click **Export to Excel** to download filtered data
- In the desktop app, a **Save As** dialog will appear — choose where to save the file
- All coded fields (e.g., sex=1 → "Male", employment=2 → "Unemployed") are automatically decoded to human-readable labels

---

## Video Tutorial

A detailed video tutorial covering installation, RCDF import, data exploration, filtering, and export is available on YouTube:

**[CBMS RCDF LGU Tool — Complete Tutorial](https://www.youtube.com/watch?v=eQyyKoewS1E)**

[![CBMS RCDF LGU Tool Tutorial](https://img.youtube.com/vi/eQyyKoewS1E/maxresdefault.jpg)](https://www.youtube.com/watch?v=eQyyKoewS1E)

---

## License Management

### How Licensing Works

- Each installation generates a unique **Machine Key** (SHA-256 fingerprint of your computer's hardware)
- A **License Key** is generated by the provider and cryptographically signed to match your specific Machine Key
- The license is verified offline on every launch — no internet connection required after activation
- Licenses can be perpetual (no expiry) or time-limited (annual subscription)
- Licenses can be scoped to specific municipalities

### Checking Your License Status

1. Log in to the app
2. Click your profile (top right) → **Profile**
3. The **License Information** section shows:
   - Current status (Active, Trial, Expired, etc.)
   - License ID
   - Licensee name
   - Expiry date
   - Machine Key

### Renewing or Getting a New License

Contact the provider with your Machine Key:
- **Email:** kyuubi.raganit.rtzverka2@gmail.com
- **Phone:** 0962 409 8673 / 0995 892 4433

---

## Admin Guide

### User Management

- **Super Admin** can create and manage users via **Admin → Users**
- Roles: `super_admin`, `admin`, `user`
- New users are created by the super admin only — no public registration

### Data Management

- **Admin → Data Management** provides:
  - **Import RCDF** — Import new municipality data
  - **Reset Database** — Wipe all data (requires password confirmation and typing `DELETE ALL DATA`)

### Custom Logo

- **Profile → Application Logo** — Upload a custom logo (PNG/JPEG/SVG/WebP, max 2MB)
- The logo appears in the app header immediately after upload

### Activity Logs

- All sensitive actions are logged: login/logout, RCDF import, data reset, user creation/deletion, role changes, license activation, failed login attempts
- Viewable via **Admin → Activity Logs**

---

## Security Features

- **Machine-locked licensing** — Licenses are bound to a specific computer and cannot be transferred
- **RSA-2048 signed licenses** — Cryptographically verified, cannot be forged
- **Automatic session timeout** — 60-minute inactivity auto-logout with 5-minute warning
- **Encrypted sessions** — All session data is encrypted
- **Strict same-site cookies** — Prevents CSRF attacks
- **Security headers** — CSP, Permissions-Policy, X-Frame-Options, etc.
- **No public registration** — Only super admin can create user accounts
- **Password policy** — Minimum 10 characters, mixed case, numbers, and symbols required
- **Audit logging** — All sensitive actions are recorded with user, IP, and timestamp

---

## Troubleshooting

### App Won't Launch

- Ensure no other instance of CBMS is running (check Task Manager for `cbms.exe`)
- Try running as Administrator (right-click the shortcut → Run as administrator)
- Check Windows Defender / antivirus — add an exclusion for the CBMS install folder if needed

### RCDF Import Fails

- Ensure you're using the correct `.rcdf` file (not a ZIP or extracted folder)
- Ensure the private key `.pem` file matches the RCDF file (same municipality code)
- Double-check the passphrase — it's case-sensitive
- Check that the municipality is selected from the dropdown
- Try the import again — the app cleans up temporary files after each attempt

### License Activation Fails

- Ensure you copied the **full** Machine Key (64 hex characters, a-f and 0-9)
- Ensure the License Key you received matches your Machine Key — licenses are machine-locked
- Contact the provider if the license key appears invalid

### App Shows "Trial Expired"

- The 14-day trial has ended — activate a license to continue
- If you already have a license, go to the activation screen and enter it

### Export Doesn't Work

- In the desktop app, a **Save As** dialog should appear when you click Export
- If no dialog appears, check if another dialog is hidden behind the app window
- Ensure you have write permission to the destination folder

---

## Support & Contact

| Channel | Details |
|---------|---------|
| Email | kyuubi.raganit.rtzverka2@gmail.com |
| Phone | 0962 409 8673 / 0995 892 4433 |
| Video Tutorial | [YouTube](https://www.youtube.com/watch?v=eQyyKoewS1E) |

---

## About

**CBMS RCDF LGU Tool** is developed and maintained by **TINAGAR**.

&copy; 2026 TINAGAR — All Rights Reserved.

This software is licensed to LGUs for their use. Unauthorized copying, redistribution, or reverse engineering is prohibited. The licensing system uses RSA-2048 cryptographic signatures to protect against unauthorized use.
