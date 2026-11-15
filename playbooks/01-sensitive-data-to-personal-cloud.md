# Playbook 01: Sensitive data uploaded to personal cloud storage

| Field | Value |
| --- | --- |
| ATT&CK | [T1567.002](https://attack.mitre.org/techniques/T1567/002/), Exfiltration Over Web Service: Exfiltration to Cloud Storage |
| Trigger | Endpoint DLP alert: file matching a sensitive information type uploaded to an unsanctioned cloud storage domain |
| Goal | Decide quickly whether this is a mistake, a policy violation, or data theft, and act in proportion |

## 1. Gather context (first 15 minutes)

| Question | Where to look |
| --- | --- |
| What data, and how much? | Alert details: sensitive info type, match count, file name and size |
| Where did it go? | Destination domain, personal or corporate account |
| Who is the user? | Role, department, manager, start date, any departure notice |
| Is this a pattern? | Prior DLP alerts for this user in the last 90 days |
| Was it blocked? | Policy action: audit only, block with override, or block |

## 2. Classify

| Signal | Likely accidental | Investigate further | Escalate |
| --- | --- | --- | --- |
| Volume | 1 file, few matches | Several files | Bulk upload or archive files |
| History | First alert | Repeat alerts | Repeat after being warned |
| Timing | Normal working hours | Off hours | Around resignation or termination |
| Override | No override | Override with a business reason | Override with no or vague reason |

## 3. Respond

- **Accidental:** notify the user and their manager, confirm the file was deleted from the personal account, and point them to the approved tool.
- **Violation:** document, notify the manager, and request written confirmation of deletion. Consider moving the policy from audit to block for this group.
- **Suspected theft:** do not tip off the user. Preserve evidence, escalate to the incident response lead, and follow HR and Legal guidance.

## 4. Close out

1. Record the classification and the evidence it was based on.
2. If the alert was a false positive, note why and feed it into policy tuning.
3. If the policy should have blocked and did not, raise a tuning request.

## Hunting query

<!-- Add a KQL query you have tested yourself for finding these uploads (for example from Purview Activity Explorer exports or your Sentinel workspace). Note which table it runs on. -->
