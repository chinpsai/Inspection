# YL Inspection Kit
Switchroom Daily Inspection Form

## Background
Commercial inspection software comes with high annual subscription fees. This lightweight web form was built to match the local switchroom and town council inspection workflow, for logging inspection records and generating PDF reports.
No expensive subscription required. It works directly on mobile phones for site staff.

## Features
- Mobile-friendly layout, fill in inspection records on site
- Form fields designed according to switchroom inspection standards
- One-click PDF export to save inspection evidence
- Pure static webpage, hosted on GitHub Pages, no backend server needed

## Technical choices & trade-offs
- Built with HTML + JavaScript, lightweight and functional under poor network conditions
- jsPDF library for PDF generation
- Free hosting on GitHub Pages, easy to share with teammates
- No fancy UI: priority is stability, simplicity and practicality for site work

## Development notes & issues resolved
These are the problems I encountered and fixed during development:
1. GitHub Pages build failure: Jekyll tried to look for a `docs` folder. Reconfigured the source to root directory and added `.nojekyll` to bypass Jekyll.
2. Codespaces free quota exhausted: switched to GitHub web editor instead of cloud development environment.
3. Repeated debugging for repository renaming, branch settings and workflow deployment errors.
4. Tuned PDF export function to output form content correctly.

## How to use
1. Open the webpage link
2. Fill in the switchroom inspection items one by one
3. Export PDF to save the inspection report for record keeping

## Roadmap
- Add mandatory field validation
- Local storage: keep unfinished form data when closing the page
- Adjust form fields continuously based on real site requirements

## License
For internal workplace inspection use only
