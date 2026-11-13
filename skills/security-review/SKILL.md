---
name: security-review
description: Produce an evidence-based security assessment and phased remediation document for an application. USE FOR security assessments, OWASP reviews, reviewing security of a running app, or creating Docs/SecurityReview.md. DO NOT USE FOR implementing security fixes, generic code review, or testing a third-party target.
---

# Application security review

Review the application's actual code and configuration, then produce an evidence-backed Markdown assessment. Do not modify source code. Test a running application only when the user explicitly authorizes a non-production target and available tools support safe verification.

## Workflow

1. Read repository guidance and identify the app's entry points, deployment model, relevant source and configuration, and tests. Do not claim to have inspected files you did not read.
2. Identify context that changes risk: deployment and hosting, internet exposure, authentication provider, data sensitivity, and compliance scope. Ask focused questions for material unknowns not answerable from code; offer recommended defaults. Never infer authorization to test a live system.
3. Review applicable areas, citing file paths and line numbers or member names:
   - authentication and session, cookie, and token configuration
   - authorization, role and policy enforcement, and resource ownership
   - injection, path traversal, unsafe deserialization, and AI prompt boundaries
   - XSS and unsafe HTML or JavaScript rendering
   - CSRF and state-changing endpoints
   - secrets and sensitive-data exposure, including logs, client bundles, responses, and source
   - HTTPS, headers, CORS, middleware ordering, and production error handling
   - data protection, cryptography, random values, and sensitive-data storage
   - uploads and downloads, input and model binding
   - logging, errors, auditability, rate limits, and denial-of-service exposure
   - SSRF and outbound-request controls
   - dependency and target-framework risks and client-side supply chain
   - framework-specific concerns, including Blazor where present, and hosting or Azure controls evidenced by the repository
4. Record only findings supported by repository evidence. Do not turn generic best practices into findings. For each finding include a unique ID, title, severity with a one-sentence rationale, applicable OWASP Top 10 2021 category or "not directly mapped", affected locations, impact and conditions, a minimal relevant snippet with sensitive values redacted, a recommended fix, and safe verification steps.
5. Create or update the review document using the repository's convention; default to `Docs/SecurityReview.md`. If it already exists, preserve useful history and ask before replacing it. Include a summary table, scope and methodology, accepted-risk notes, relevant architecture, authentication and request-flow diagrams, detailed findings, prioritized remediation phases, and recommended security tests. Include a dependency vulnerability report only when its output is available; do not imply a scan was run when it was not.
6. When permitted, ask `security-reviewer` for an independent, read-only check of the report and cited code. Have it look for unsupported claims, missed high-impact paths in the stated scope, incorrect severity, unsafe recommendations, and exposed sensitive values. Incorporate valid feedback. If unavailable, perform a separate skeptical pass and say so.
7. Re-open cited locations and confirm findings and fixes are accurately described. Report the document path, key findings and severity counts, unaddressed review notes, unreviewed areas, and tests or scans not run.

## Safety and privacy

- Never print or copy secret values into the report, chat, logs, or screenshots. Redact examples. Do not silently exempt secrets merely because they are in a private repository or configuration file: assess whether they are exposed, committed, client-delivered, logged, or otherwise at risk, and report relevant exposure without reproducing values.
- Do not access production data, use real credentials, make destructive changes, or probe a live or third-party service. Ask before active runtime validation; restrict it to an explicitly authorized, isolated non-production environment. Prefer source-based reasoning and non-destructive tests.
- Describe a vulnerability and its remediation without providing a reusable attack playbook or instructions for exploiting an unrelated target.
- Do not modify application source code. The report's remediation plan is not permission to implement fixes.
- Mark a review area "not assessed" when evidence or authorized access is unavailable; state what is missing.

## Finding quality

A finding must identify the condition in this application, show where it occurs, explain its realistic impact, and give a feasible fix and verification method. Avoid speculative findings, duplicates, and severity inflation. Be explicit about assumptions and environmental dependencies.
