# Inspection
Inspection modules
By 曾炳胜
# Switchroom Daily Inspection – Mobile Input Module

A lightweight, mobile-first web form for recording **daily switchroom inspections** on site. Designed to replace paper checklists and expensive commercial PDA apps.

- Fill the form directly on a phone in the switchroom
- Works on any modern phone browser — no app installation, no licence fee
- Generates a clean inspection report (PDF / print-ready) with photos and signature

---

## 1. Purpose

Site staff perform daily checks on switchrooms. The results are usually written on paper forms, then retyped into Excel or Word later. This module removes the double work:

1. Walk into the switchroom, open the form on the phone
2. Tick the checklist, key in meter readings, take photos
3. Submit — the record is stored and a report is produced immediately

**Target users:** site technicians, electricians, facility / building maintenance staff, contractors doing routine inspection.

---

## 2. Key Features

| Feature | Description |
|---|---|
| Mobile-first form | Single-column layout, large tap targets, thumb-friendly |
| Checklist items | Pass / Fail / Not Applicable per item, with remarks |
| Meter readings | kWh, voltage (L1/L2/L3), current, power factor, maximum demand |
| Photo capture | Camera upload per section, auto-compressed before upload |
| Signature | On-screen signature by the inspecting technician |
| Offline draft | Records kept locally until network is available |
| Report output | Structured PDF / printable report with header, readings, photos, signature |
| Record history | Each inspection stored with date, time, room ID, inspector name |

---

## 3. Inspection Checklist Scope

The form follows the usual daily switchroom routine:

**A. Switchroom Condition**
- Room clean and free of obstructions
- No water ingress / dampness / leakage
- Door, lock and access control in order
- Lighting and ventilation working
- Fire extinguisher present, within expiry, pressure OK
- Signage, danger notice and room identification plate present
- No pest / rodent activity

**B. Switchgear & Panel**
- Panel front cover closed, no damage
- No abnormal noise, vibration or smell
- No discolouration, burnt marks or overheating signs
- Indicator lamps and panel meters functioning
- Switch position recorded (ON / OFF / AUTO)
- Cable terminations and glands secure
- Earth / bonding conductor intact
- Labels and circuit identification legible

**C. Meter Readings**
- kWh reading (cumulative)
- Voltage L1 / L2 / L3
- Current L1 / L2 / L3
- Power factor
- Maximum demand
- CT ratio / meter multiplier (if applicable)

**D. Protection & Devices**
- Earth leakage relay test button functional
- Protection relay no alarm / trip indication
- Battery charger and batteries healthy (if fitted)
- UPS status normal (if fitted)

**E. Housekeeping & Safety**
- Rubber mat in place and dry
- PPE available (gloves, boots, face shield)
- Test instruments present and calibrated
- Key register updated on entry / exit

---

## 4. Recommended Workflow

```
Open form on phone
   ↓
Select Town Council / Site / Room ID
   ↓
Fill checklist  →  any "Fail" prompts a remark + photo
   ↓
Key in meter readings
   ↓
Capture photos of panel, meter, switchroom condition
   ↓
Sign on screen
   ↓
Submit  →  record saved + report generated
```

---

## 5. Suggested Data Model

```
inspection_record
├── id
├── council            (MYTTC / WCTC / SKTC / ...)
├── site_name
├── room_id
├── inspection_date
├── inspection_time
├── inspector_name
├── inspector_contact
├── checklist[]        { item_code, result(P/F/NA), remark }
├── readings           { kwh, volt_l1, volt_l2, volt_l3,
│                        amp_l1, amp_l2, amp_l3,
│                        power_factor, max_demand, ct_ratio }
├── photos[]           { section, file_url }
├── signature_url
├── overall_status     (Normal / Follow-up Required)
└── submitted_at
```

---

## 6. Suggested File Layout

```
/
├── index.html          # main inspection form
├── css/style.css       # mobile layout
├── js/app.js           # form logic, validation, draft saving
├── js/report.js        # report / PDF generation
├── assets/             # icons, logo
└── README.md
```

---

## 7. Getting Started

1. Clone the repository
   ```bash
   git clone https://github.com/<username>/<repo-name>.git
   ```
2. Open `index.html` in a browser, or serve locally:
   ```bash
   python -m http.server 8000
   ```
3. On the phone, open `http://<your-ip>:8000` over the same Wi-Fi to test.

---

## 8. Deployment

Static hosting via **GitHub Pages**:

1. Repository → **Settings** → **Pages**
2. Source: `Deploy from a branch` → branch `main` → folder `/ (root)`
3. Save, wait 1–3 minutes
4. Site live at `https://<username>.github.io/<repo-name>/`
5. `https://chinpsai.github.io/Inspection/`

> Remember: if the repository is renamed, the Pages URL changes.

---

## 9. Notes on Use

- Take readings **before** touching any switch — record first, operate later
- Any "Fail" item must include a photo and a remark
- Photos should show the panel label / meter display clearly
- Never bypass an earth leakage or protection trip without authorisation
- Inspection record is an audit document — do not edit after submission

---

## 10. Roadmap

- [ ] QR code scan for room identification
- [ ] Multi-language labels (EN / 中文)
- [ ] Automatic comparison with previous reading (flag abnormal jump)
- [ ] Batch export monthly summary
- [ ] Role-based access (technician / supervisor approval)

---

## 11. Disclaimer

This tool records inspection results only. It does not replace statutory testing, licensed electrical work, or the site's approved safety procedure. Always follow the site PTW (Permit To Work) and safety requirements.

---

## Contact

Maintained by: 曾炳胜
Purpose: internal site inspection record keeping
