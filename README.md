# clinicKU — Clinic Dashboard and Registration

A single-page clinic management web app for **The Savior Malaysia**, built for clinic staff, doctors, pharmacists, and cashiers. It runs entirely in the browser — **no backend, no database, no login, no payments integration**. Everything happens on one page with instant, on-screen updates.

![Tech](https://img.shields.io/badge/tech-HTML%20%7C%20CSS%20%7C%20JavaScript-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## Features

### Patient (single page, full CRUD)
- **Register / Edit / Delete** patients with name, visit type, phone, email, and address.
- **Today's Queue** with color-coded status, consultation room assignment, status dropdowns, and one-tap **Call** (`tel:`) and **WhatsApp** (`wa.me`, auto-normalized to Malaysian +60 format) contact buttons.
- **Patient Profile** with full details, diagnosis, doctor's remarks, and medication dispensing records (dispense / mark pending).
- A patient whose payment is completed shows a blue **✓ Paid** badge with check icon.

### Doctor (single consultation page)
- **Diagnosis** and **Remarks** per patient (saved to their profile).
- **Prescription** with medication selected from live inventory (with stock counts), dosage, and supply — items flow to Pharmacy on save.
- **Medical Certificate (MC)** generation with certificate number, rest-period dates, remarks, and staff signature block.
- **All Consultations** summary list.

### Pharmacy
- **Dispensing**: patient dropdown showing the medication that needs to be supplied/dispensed, per-item QR code, **Dispense** button (auto-deducts inventory stock and auto-advances the patient's queue status), and **scan-to-verify** by code.
- **Medication Inventory**: full **CRUD** (add / edit / delete) with auto-generated stock codes (`TSV-TYPE-####` derived from medication type), stock levels, reorder levels, and color-coded In stock / Low stock / Out of stock tags.

### Cashier
- **Payment (one page)**: next-patient-to-pay dropdown with suggested amount (visit + medication, incl. 6% service tax), editable amount, document choice (**Quotation / Invoice / Receipt**), payment method, post-payment status update (defaults to **Paid**), and instant document generation.
- Standalone **Quotation / Invoice / Receipt** pages, each producing a formatted sample document with document number (`TSV-QUO/INV/RCP-YYYY-#####`), itemized lines, totals, and status stamps (PRICE ESTIMATE / PAYMENT DUE / PAID).

### Patient journey tracker
At the top of the Doctor, Pharmacy, and Cashier pages there is a visual **5-stage pipeline with icons** — Registered → Diagnosis → Prescribed → Dispensed → Paid — showing **Fulfilled / Next step / Pending** for the selected patient, updating live so every role can see what still needs to be done.

### Design
- Floating single-line header with **clinicKU** serif brand (`#0000FF` blue), Montserrat body typography, and inline SVG icons.
- Dark grey text, blue action buttons with white icons/text, clean white pages.
- Logged-in staff avatar next to the date (hover to reveal name/role, click for the employee profile panel).
- Footer with today's date and *"© The Savior Malaysia · www.thesaviorofficial.com · All Rights Reserved"*.

---

## Getting started

No build step, no dependencies, no framework.

1. Download or clone this repository.
2. Open `index.html` in any modern browser — that's it.

Or serve it locally (optional):

```bash
# Python
python -m http.server 8080
# then visit http://localhost:8080
```

## Deployment (GitHub Pages)

1. Push this repository to GitHub (see below).
2. In the repository, go to **Settings → Pages**.
3. Under *Build and deployment*, choose **Deploy from a branch**.
4. Select branch `main` and folder `/ (root)`, then save.
5. The site will be live at `https://<your-username>.github.io/<repo-name>/` within a few minutes.

## Repository structure

```
.
├── index.html    # The entire app (HTML + CSS + JavaScript, self-contained)
└── README.md     # This documentation
```

## Sample data

The app opens with three Malaysian sample patients (Ahmad Zulkifli bin Hassan, Siti Nurhaliza binti Abdullah, Lim Wei Jian) and six inventory items so it is never empty. **All data is generated sample data for demonstration** — document amounts are not real charges, and the medical certificate is not a valid medical document. Nothing is saved between visits; refreshing resets to sample data.

## Privacy notes

- **Call** buttons use `tel:` links; **WhatsApp** buttons open `wa.me` with a pre-filled status message in a new tab.
- No data ever leaves the browser — there is no server, no analytics, and no storage.

## License

MIT © The Savior Malaysia
