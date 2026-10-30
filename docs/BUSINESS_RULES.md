# Business rules (from the requirement document)

## Employee data
- PAN: 5 letters, 4 digits, 1 letter (regex). Aadhaar: 12 digits, never shown unmasked in the UI.
- UAN: 12 digits, optional for new joiners. IFSC: 4 letters, then 0, then 6 letters/digits (11 chars).
- Mobile: 10 digits starting 6-9. PIN: 6 digits. State: dropdown of Indian states and UTs.
- Date of birth must make the employee at least 18 on the date of joining.
- Employee code auto-generated, e.g. KCF0001; never changes.
- An employee cannot report to themselves or to someone who reports to them (no loops).
- Masking: PAN `ABCDE****F`, Aadhaar `XXXX XXXX 1234`, bank account last 4 digits.
- Deactivation sets a last working day; record is never deleted; no login after that date.
- Every change to job or statutory fields is audit-logged (who, what, old, new, when).

## Attendance
- Times in IST. One record per employee per day.
- Head office (Panaji): Mon-Fri, weekly off Sat+Sun. Plant (Verna): Mon-Sat, weekly off Sun.
- Worked >= 8h Present; 4h to <8h Half Day; <4h or no punch Absent.
- Check-in after 10:15 AM is Late. 3 Lates in a calendar month = 1 half-day LOP.
- A day with approved leave is On Leave even if the employee punched in.
- WFH counts as Present. Statuses: Present, Half Day, Absent, On Leave, Holiday, Weekly Off.
- Regularisation: employee requests correction with a reason; manager approves/rejects; attendance changes only after approval.
- Holidays are per location, typed National / State / Optional.

## Leave policy (leave year Jan-Dec)
| Type | Quota | Accrual | Carry forward | Half day |
|---|---|---|---|---|
| Casual (CL) | 8 | Credited 1 Jan, pro-rated for joiners | Lapses 31 Dec | Yes |
| Sick (SL) | 7 | Credited 1 Jan, pro-rated for joiners | Lapses 31 Dec | Yes |
| Earned (EL) | 15 | 1.25 per completed month | Up to 30 days | No |
| Maternity | Per Maternity Benefit Act (verify in research) | On request | N/A | No |
| Paternity | 5 (company policy) | On request | N/A | No |
| Loss of Pay | Unlimited | N/A | N/A | Yes |

- No leave with insufficient balance; app offers to convert the excess to LOP.
- SL over 2 consecutive days needs a medical certificate upload.
- Leave days = working days only (location weekly offs and holidays excluded). No sandwich rule.
- Cannot apply for leave more than 30 days in the past.
- Balance changes only on approval. Cancel pending, or approved-not-started leave, restores balance.
- Managers cannot approve their own leave. Manager emailed on new request; employee emailed on decision.
- "Available balance" should be calculated, not stored (decide and justify in ARCHITECTURE.md).

## Roles
Only an HR Admin flag is stored. Manager = anyone who is reporting_manager_id of an active employee.
See the permission table in the requirement document (employee / manager / HR).

## Month-end CSV (HR)
Employee code, name, days present, WFH days, leave days by type, LOP days, holidays, weekly offs.
