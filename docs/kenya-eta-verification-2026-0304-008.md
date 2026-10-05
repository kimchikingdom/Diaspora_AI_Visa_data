# Kenya eTA verification (bounty-2026-0304-008)

Issue #3. Scope is every foreign route into Kenya (`* -> KE`), not a single origin.

Checked on 2026-10-05, official pages only:

- https://etakenya.go.ke/general-information
- https://etakenya.go.ke/faqs
- https://etakenya.go.ke/eligibility

## What the portal says

- Most travellers need an eTA before they fly. The government fee is **USD 30**. Any card or bank surcharge is on top of that.
- Apply at least **3 days** before travel. The approval email is the thing the airline will want to see. Do not treat this as same-day processing.
- A standard approval is **single entry**, valid **90 days from issue**, for a stay of up to **90 days**.
- The only application URL to store is https://etakenya.go.ke/. Lookalike sites add their own service fee.

## Who is exempt

Citizens of the East African Partner States listed on the eligibility page do not need an eTA: Burundi (BI), DR Congo (CD), Rwanda (RW), South Sudan (SS), Tanzania (TZ), and Uganda (UG). Somalia is an EAC member but is **not** marked exempt in this claim; add it only if the eligibility page names it.

Also exempt, per that same page (2025 categories included): Kenya permanent residents and valid work-permit or pass holders, valid Kenya re-entry pass holders, airside transit passengers who do not leave the airport, on-duty airline or ship crew named on the manifest, on-duty private-aircraft crew in transit, diplomatic or official passport holders on official duty (by arrangement, not a blanket waiver), and accompanied children under 16.

These categories come from the portal as it stood on the access date. The gazette is not copied here. Anyone changing a route should open the eligibility page again first.

## What this patch does not do

`data/kenya_eta_verification_2026-0304-008.json` is the machine-readable note: default `eta_required: true`, fee 30, processing 3 days, and `eta_required: false` only on `BI_KE`, `CD_KE`, `RW_KE`, `SS_KE`, `TZ_KE`, and `UG_KE`.

Individual files under `data/passport-requirements/` are left as they are, so this claim can be reviewed on its own before those routes are bulk-updated. Nothing was submitted on the eTA portal, and no existing route file was deleted.

Suggested policy label for a non-exempt origin is `eVisa`, matching the eTA column already used in the coverage table.
