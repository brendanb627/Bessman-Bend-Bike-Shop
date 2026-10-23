# Design Document Review

## 1. Logical Issues
- **Contradictory account requirements:** "Require an account" is listed as a non-goal, but guest reservations are explicitly supported. Clarify whether accounts are optional or excluded entirely.
- **Unclear replacement charges:** Automated replacement charges are a non-goal, yet charging replacement fees is included in the use cases. Clarify whether charges require employee approval.
- **Unclear cancellation scope:** Automated closure-day cancellations are excluded, but a use case allows managers to cancel all reservations for today. Clarify whether manual bulk cancellation is intended.
- **Missing rental workflows:** The README describes rental extensions, per-bike late fees, and resuming unfinished reservations, but these are not represented in the use case diagrams.

## 2. Structural and Diagram Issues
- **Incomplete actor list:** Employee appears throughout the diagrams but is missing from the Actors section.
- **Incorrect or ambiguous relationships:** Some arrows imply that customers initiate bulk cancellations or employees participate in payment processing in ways that are not clearly defined.
- **Missing reservation flow:** The diagrams do not show how availability is checked before a reservation is confirmed or how overlapping bookings are prevented.
- **Duplicate UX diagrams:** The customer charges flow appears twice.
- **Missing error paths:** The UX diagrams show successful actions but omit failures such as declined payments and unavailable bikes.

## 3. Requirements and Documentation Issues
- **Incomplete statements:** The inventory capacity requirement and employee training assumption end mid-sentence. There are also spelling errors, such as "Overiew" and "shuold."
- **Vague non-functional requirements:** Uptime, browser compatibility, and data synchronization lack measurable criteria.
- **Unclear permissions:** The document does not consistently define which roles can manage permissions, issue refunds, or apply fees.
- **Missing technical design:** No data model or architecture explains how bikes, reservations, payments, and inventory synchronization relate.

## 4. Recommended Priorities
1. Resolve contradictory requirements and clarify employee permissions.
2. Document the core reservation, payment, return, and extension workflows.
3. Correct the actor relationships and remove duplicate UX diagrams.
4. Complete unfinished requirements and define measurable acceptance criteria.
5. Add a basic data model and system architecture.

## Overall Assessment

The document is a good starting point, but its biggest weakness is the lack of consistent rules connecting inventory, reservations, payments, and rental returns. Resolve those rules first, then update the diagrams to reflect the agreed-upon behavior.