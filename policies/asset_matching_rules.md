# Tessmar Facility Services: Asset Matching Rules (fictional)

Simplified, fictional rules. Cite them by section, for example "Matching 2.2".

## 1. Exact matches (code)

1.1 A record or document line belongs to an asset when its tag is exactly the same as the construction register's asset ID.
1.2 Code links exact matches automatically. Nothing else is linked automatically.

## 2. Possible matches (agent)

2.1 When a tag differs only in format (for example missing leading zeros, spaces, or dashes: "AHU-14" and "AHU-014"), code marks it as a **possible match** and does not link it.
2.2 The agent may confirm a possible match as the **same asset** only when at least two of model, serial and location agree with the construction register and none of them conflict. It must say which attributes agree.
2.3 A confirmed naming difference is a minor exception (Readiness 4.3). The contractor is asked to correct the tag on the document at the next issue.

## 3. Uncertain matches (escalate)

3.1 If attributes conflict, are missing, or point to more than one asset (for example the tag suggests one unit and the location suggests another), the match is **uncertain**. The agent must not merge the records. It escalates and asks the contractor to verify on site (Escalation 2.2).
3.2 Never guess a serial number, a tag or a location that no source states.

## 4. Serial numbers

4.1 Serial numbers are compared exactly by code. A difference of even one character is a conflict.
4.2 The agent may suggest a likely cause (for example two digits swapped), but it must not decide which serial is correct. Both records are kept unchanged until the manufacturer confirms.
