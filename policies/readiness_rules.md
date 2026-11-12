# Tessmar Facility Services: Asset Readiness Rules (fictional)

Simplified, fictional rules for a prototype. Cite them by section, for example "Readiness 2.3".

## 1. Purpose and scope

1.1 These rules decide whether an asset handed over by the contractor is ready for the FM team's acceptance review. They apply to every asset in the construction asset register.
1.2 The planned handover date for Sarava Tower is **24 November 2026**. Warranty and date checks use this date.
1.3 Passing these rules means "ready for review", never "accepted". Formal acceptance is signed by the FM handover manager outside this tool (Escalation 1.1).

## 2. Evidence every asset needs

2.1 **FM record:** the asset exists in the FM register (CAFM import), with the same tag.
2.2 **Commissioning:** a commissioning certificate lists the asset by its exact tag, with Result: Pass and Final approval: Signed.
2.3 **Warranty:** a warranty certificate lists the asset by its exact tag, with the same serial number as the construction register, and an expiry date after the handover date (1.2).
2.4 **O&M manual:** an O&M manual lists the asset in its "Covers" line.
2.5 **Maintenance plan:** the FM register shows a preventive maintenance (PPM) plan for the asset, not "Not configured".
2.6 **Consistent identity:** model, serial and location agree across the construction register, equipment schedule, FM register and documents.

## 3. Readiness status

Code applies these in order. The first that matches is the status.

3.1 **Not ready for acceptance:** a critical exception is open. Critical means: commissioning not approved (2.2), a life-safety asset (fire systems, lifts, standby generator) with any open exception, or a request to accept outside these rules (Escalation 2.4).
3.2 **Conflicting information:** two sources disagree on model, serial or location (2.6), or a document cannot be matched to one asset with confidence (Matching 3.1).
3.3 **Missing required evidence:** any item in section 2 is missing or unclear.
3.4 **Pending contractor clarification:** a clarification request has been approved by the FM handover manager and is waiting for a reply. Only a person sets this status.
3.5 **Ready for review:** every check in section 2 passes.

## 4. Severity of exceptions

4.1 **Critical:** see 3.1.
4.2 **Major:** serial or location conflict, missing or expired warranty, missing O&M manual, missing FM record, unresolved asset match.
4.3 **Minor:** naming differences that are confirmed to be the same asset (Matching 2.2), or a missing PPM plan, which the FM team fixes itself.

## 5. Who fixes what

5.1 Commissioning certificates and approvals: the installing subcontractor, through the main contractor (Halvorn Contracting).
5.2 Warranty corrections: the manufacturer, through the installing subcontractor.
5.3 O&M manuals: the installing subcontractor.
5.4 FM register records and PPM plans: the FM team's CAFM administrator (internal, no contractor request needed).
5.5 Location or tag conflicts: the main contractor confirms on site; the FM team corrects its own register if it is wrong.
