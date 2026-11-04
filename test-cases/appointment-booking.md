# Appointment Booking: Manual Test Cases

## Test approach

These cases cover a sample appointment booking flow. They are written as a portfolio exercise and have not been executed against a live application. Adapt the assumptions and record observed results before presenting execution status.

## Sample workflow assumptions

- A visitor selects an appointment type, date, and available time, then enters contact details and submits.
- Required fields are appointment type, date, time, name, and email.
- The application blocks dates in the past and times that are no longer available.
- A successful booking displays a confirmation with a reference number and the selected appointment details.
- Validation errors explain what needs attention and preserve valid entries.
- This sample scope does not define payment, account creation, cancellation, or rescheduling.

**Test data**


Use a future date with at least two available slots, a valid email such as `qa.sample@example.com`, and a malformed email such as `qa.sample`. Replace these with permitted test data in the target environment.

### APPT-001 — Load available appointment types

**Steps:**
1. Open the booking page.
2. Review the appointment type choices.

**Expected result:** The page loads without an error. Appointment types are visible, understandable, and selectable.


**Execution:** Pass  
**Actual result:** Appointment types loaded without error and were visible, understandable, and selectable.  
**Environment:** Pretend sample page  
**Date:** November 4, 2026
### APPT-002 — Show availability for a future date

**Priority:** P1 · **Type:** Functional 

**Preconditions:** At least one future date has availability.

**Steps:**
1. Select an appointment type.
2. Choose a future date with known availability.

**Expected result:** Available time slots for that date are displayed. Unavailable times are not presented as selectable.



**Execution:** Pass  
**Actual result:** Time slots that are shown are available. Unavailable time slots are not present or selectable.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-003 — Complete a valid booking

**Priority:** P1 · **Type:** Positive 

**Preconditions:** A future slot is available.

**Steps:**
1. Select an appointment type, future date, and available time.
2. Enter a name and valid email.
3. Submit the booking.

**Expected result:** The booking is accepted once. A confirmation shows a reference number, appointment type, date, time, and contact details or an appropriate privacy-safe summary.


**Execution:** Pass  
**Actual result:** The booking is accepted once. A confirmation is shown with reference number, date, time, appointment type, contact details and other privacy-safe summary details.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-004 — Submit with required fields empty

**Priority:** P1 · **Type:** Negative 

**Preconditions:** Booking form is open.

**Steps:**
1. Leave all required fields empty.
2. Submit the form.

**Expected result:** The booking is not created. Each missing required field is identified with a clear message, and focus or an error summary helps the user find the issue.


**Execution:** Pass  
**Actual result:**  The booking is not completed. Each empty field is identified with a clear message, and an error message helps the user find the missing information.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-005 — Validate malformed email

**Priority:** P1 · **Type:** Negative 

**Preconditions:** A future slot is available.

**Steps:**
1. Complete all required fields.
2. Enter `qa.sample` as the email.
3. Submit the form.

**Expected result:** The booking is not created. The email field receives a clear validation message, and other valid entries remain populated.


**Execution:** Pass
**Actual result:**  The booking was not created. The email field showed a validation message, and no success toast appeared.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-006 — Reject a date in the past

**Priority:** P1 · **Type:** Boundary 

**Preconditions:** Booking form is open.

**Steps:**
1. Attempt to select yesterday or enter a past date if direct date entry is supported.
2. Continue or submit.

**Expected result:** A past date cannot be booked. The user receives a clear explanation and can choose a valid date.


**Execution:** Pass  
**Actual result:**  Only future valid dates can be selected and booked. The user receives a clear explanation and can choose an available date.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-007 — Prevent booking a slot that became unavailable

**Priority:** P1 · **Type:** Negative / concurrency · 

**Preconditions:** A slot can be made unavailable after it is displayed, for example by booking it in a second session.

**Steps:**
1. In session A, select an available slot and complete the form without submitting.
2. In session B, book that same slot successfully.
3. Submit the booking in session A.

**Expected result:** The system does not create a conflicting booking. It explains that the slot is no longer available and lets the user select another time without losing appropriate form entries.


**Execution:** Pass  
**Actual result:**  The system does not create a conflicting booking. It explains the space is no longer available and allows the user to select another time without losing form entries.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-008 — Avoid duplicate booking on repeated submit

**Priority:** P1 · **Type:** Reliability 

**Preconditions:** A future slot is available.

**Steps:**
1. Complete a valid booking form.
2. Submit once, then quickly submit again or activate the submit control repeatedly while the first request is processing.

**Expected result:** Only one booking is created. The interface indicates processing and prevents accidental duplicate submissions, or safely handles repeated requests.


**Execution:** Pass  
**Actual result:**  Only one booking is created. The interface shows processing and prevents duplication.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-009 — Navigate and submit using keyboard only

**Priority:** P2 · **Type:** Accessibility / usability · **Status:** Run

**Preconditions:** Booking page is open.

**Steps:**
1. Use Tab and Shift+Tab to move through controls.
2. Use keyboard controls to select appointment details and enter contact information.
3. Submit without using a mouse.

**Expected result:** All interactive controls are reachable and operable by keyboard. Focus is visible and follows a logical order. Validation and confirmation are available to keyboard users.


**Execution:** Pass  
**Actual result:**  All interactive controls are reachable by keyboard. Focus is visible and follows a logical order. Confirmation and validation are available to keyboard users.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

### APPT-010 — Handle temporary availability service failure

**Priority:** P2 · **Type:** Error handling 

**Preconditions:** A test environment can simulate an availability service error or network interruption.

**Steps:**
1. Open the date or time selection step.
2. Simulate the availability request failing.
3. Observe the page and retry if a retry action is offered.

**Expected result:** The page does not show stale or misleading availability as confirmed. A plain-language error and recovery option are provided, and the user can retry.


**Execution:** Pass  
**Actual result:** The page does not show misleading availability as confirmed. An error message and retry option are provided.
**Environment:** Pretend sample page  
**Date:** November 4, 2026

## Execution record template

Copy this table for each execution cycle. Attach screenshots or other evidence using the team's approved storage and privacy practices.

| Case ID | Build / environment | Result (Pass / Fail / Blocked) | Actual result | Evidence / defect link | Tester | Date |
| --- | --- | --- | --- | --- | --- | --- |
| APPT-001 |  |  |  |  |  |  |
