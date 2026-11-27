# Manual Accessibility & Native Validation Audit — `cod-landing-page/`

**Date:** 2026-11-27  
**Environment:** Windows 11 · Microsoft Edge (InPrivate) · Windows Narrator (`Win + Ctrl + Enter`)  
**Target Component:** `#intel-briefing` Subscription Form (`#form`, `#email`, `#submit`)

## Observations & Recovery Behavior

1. **Landmark, Label & Format Hint Pairing:**
   - Entering the form announces the `<section>` landmark (`Join The Intel Briefing region`), the explicit `<label for="email">` (`Operator Email Address (Required), edit`), the linked `aria-describedby="email-hint"` instruction (`Format: name@domain.com. Your typed address is preserved automatically if validation flags an error.`), and native `required` + `autocomplete="email"` states (`Required, has popup`).
2. **Test Case 1 — Empty Required Field Submission:**
   - Activating `JOIN THE SQUAD` (`#submit`) with `#email` blank blocks submission, returns focus directly to `#email`, and announces: `Please fill out this field. Required`.
3. **Test Case 2 — Invalid Email Address Submission (`Operator@`):**
   - Submitting `Operator@` returns focus to `#email`, exposes the `Invalid` state, preserves the typed string (`Operator@`) without clearing the field, and announces: `Please enter a part following '@'. 'Operator@' is incomplete.`
   - *Browser Behavior Note:* Once native validation is triggered in Microsoft Edge, constraint feedback updates dynamically as the user types (`Please include an '@' in the email address...` transitioning to `Please enter a part following '@'...`), allowing immediate in-place correction.

## Verbatim Windows Narrator Speech Log

```text
Starting Narrator
Call of Duty: Warzone — Tactical Operations & Loadout Hub and 1 more page - [InPrivate] - Microsoft Edge window, Join The Intel Briefing region, Operator Email Address (Required), edit, Format: name@domain.com. Your typed address is preserved automatically if validation flags an error., Required, has popup,
Scan
Narrator window heading level 1,
Welcome to Narrator
Call of Duty: Warzone — Tactical Operations & Loadout Hub and 1 more page - [InPrivate] - Microsoft Edge window, Join The Intel Briefing region, Operator Email Address (Required), edit, Format: name@domain.com. Your typed address is preserved automatically if validation flags an error., Required, has popup,
Scan Off
JOIN THE SQUAD, button,
Scan
Operator Email Address (Required), edit, Format: name@domain.com. Your typed address is preserved automatically if validation flags an error., Required,
Scan Off
Please fill out this field.
Required
cap O
Please include an '@' in the email address. 'O' is missing an '@'.
p
Please include an '@' in the email address. 'Op' is missing an '@'.
e
Please include an '@' in the email address. 'Ope' is missing an '@'.
r
Please include an '@' in the email address. 'Oper' is missing an '@'.
a
Please include an '@' in the email address. 'Opera' is missing an '@'.
t
Please include an '@' in the email address. 'Operat' is missing an '@'.
o
Please include an '@' in the email address. 'Operato' is missing an '@'.
r
Please include an '@' in the email address. 'Operator' is missing an '@'.
@
Please enter a part following '@'. 'Operator@' is incomplete.
JOIN THE SQUAD, button,
Scan
Operator Email Address (Required), edit, Operator@, Format: name@domain.com. Your typed address is preserved automatically if validation flags an error., Required, Invalid,
Suggestions available
Scan Off
Please enter a part following '@'. 'Operator@' is incomplete.
```