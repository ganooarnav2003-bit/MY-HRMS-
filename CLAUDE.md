# HRMS for Konkan Coastal Foods (student project)

A working HRMS for a 180-person Indian company (head office Panaji, plant Verna, Goa).
Modules: Employee Master, Attendance, Leave, and an AI HR assistant agent.
Payroll, recruitment, performance, biometrics, shifts, mobile app and multi-tenancy are OUT OF SCOPE.

## Rules for Claude Code
- Business rules live in `docs/BUSINESS_RULES.md`. Follow them exactly.
- Follow `ARCHITECTURE.md` and `DESIGN.md`. If the build must depart from them, update the file and its decision log FIRST.
- ALL dates and times are stored and shown in IST (Asia/Kolkata), whatever the server time zone.
- Role checks happen on the server, never only by hiding buttons.
- Never commit secrets. Use `.env.local`; keep `.env.example` blank.
- Aadhaar, PAN and bank numbers are always masked, in the UI and in CSVs, unless HR clicks Reveal (logged). Never send them to the AI model.
- Never run database resets or commit `.env` files without the user's approval.
- Start each checkpoint in plan mode. Write tests from the checklist before the feature.
- The student writes RESEARCH.md, ARCHITECTURE.md and DESIGN.md. Critique them; do not write them.

## Stack
(Fill in after ARCHITECTURE.md is signed off.)

## Folder rules
(Fill in after ARCHITECTURE.md is signed off.)
