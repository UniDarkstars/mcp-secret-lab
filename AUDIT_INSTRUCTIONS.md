# Secret Scanning Audit Report Template

This file defines the standard audit workflow and report format for the repository security review.

## Objective

Generate a public Secret Scanning audit summary for this repository.

The report is intended for public review and must not expose raw secrets, tokens, credentials, private keys, or complete raw Secret Scanning alert JSON.

## Report fields

For each Secret Scanning alert, include only the following fields:

| Field              | Description                        |
| ------------------ | ---------------------------------- |
| Alert Number       | Secret scanning alert number       |
| State              | Current alert state                |
| Secret Type        | Type of detected secret            |
| File Path          | File where the secret was detected |
| Line Number        | Line where the secret was detected |
| Validity           | Validity status if available       |
| Remediation Advice | Recommended remediation steps      |

## Redaction rule

Do not include the raw `secret` value in any output.

If the source alert contains a field named `secret`, replace its value with:

```text
[REDACTED]
```

Do not include raw tokens, API keys, credentials, private keys, or complete raw alert JSON in the final report.

## Gist artifact requirement

Save the final sanitized audit summary as a GitHub Gist artifact.

The Gist must contain only the sanitized audit summary, not the complete raw Secret Scanning alert JSON.

Use the following Gist settings:

* Filename: `security-audit-report-control.md`
* Description: `Sanitized Secret Scanning audit report control`
* Visibility: Public

## Expected output format

The final Gist content should use the following Markdown structure:

```markdown
# Secret Scanning 安全审计摘要

**Repository:** `<owner>/<repo>`

## Summary

| Alert Number | State | Secret Type | File Path | Line Number | Validity | Remediation Advice |
|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... |

## Notes

- Raw secret values are not included.
- Any secret value returned by the alert API must be replaced with `[REDACTED]`.
- This report is a sanitized public audit summary.
```
