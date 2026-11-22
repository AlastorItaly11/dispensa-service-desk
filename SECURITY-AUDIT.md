# Baseline repository audit

Date: 2026-11-21  
Scope: `AlastorItaly11/dispensa-service-desk` at commit `8c3e502d01bdda7c2cce6d957c3a0163f96a0771`

## Executive assessment

The repository contains one README and one self-contained static HTML file. No package manager, external script, remote stylesheet, API call, issue, pull request, release, or existing GitHub Actions workflow was observed. No obvious embedded credential or private key was observed in the inspected files.

The principal verified governance weakness is that `main` is not protected and no repository ruleset is configured. The repository also lacked automated checks and a documented security policy at the audited commit.

## Findings

### Medium — Default branch lacks protection

Evidence: the GitHub branch listing reported `main` with `protected: false`; the repository rulesets endpoint returned an empty list.

Impact: an accidental or compromised direct push can change the published site without review or required checks.

Recommendation: configure a ruleset for `main` requiring pull requests, at least one approval where available, successful audit checks, blocked force-pushes, and blocked deletions. Keep administrative bypass narrowly controlled.

Status: verified. The connected integration could not read the branch-protection detail endpoint (HTTP 403), but the branch and ruleset evidence above is conclusive for the observed state.

### Low — No automated repository checks

Evidence: no `.github/workflows` directory was present at the audited commit.

Impact: malformed HTML, obvious credential material, and unsafe repository changes may reach the published branch without automated detection.

Recommendation: add a least-privilege workflow for structural HTML checks, baseline secret-pattern detection, and repository policy checks.

Status: addressed by the proposed pull request; effectiveness must be confirmed by the first successful workflow run.

### Low — Safety-sensitive wording is incomplete

Evidence: the electrical safety section gives short practical instructions but does not clearly state that live electrical work must be performed only by qualified personnel under applicable procedures and law.

Impact: readers could interpret educational material as operational authorization.

Recommendation: add a prominent qualification and emergency/safe-isolation disclaimer after review by a competent subject-matter expert.

Status: verified; not automatically changed because content and legal positioning require owner approval.

### Low — Accessibility assurance is incomplete

Evidence: the page uses custom tab buttons and hides sections through inline styles, but does not implement the ARIA tab pattern, focus-state management, or automated accessibility testing.

Impact: keyboard and assistive-technology users may receive an incomplete navigation experience.

Recommendation: implement semantic tab roles and state, predictable focus behavior, visible focus styles, and validate with both automated and manual keyboard/screen-reader checks.

Status: verified by source inspection; runtime assistive-technology testing was not performed.

## Residual risks and limits

- GitHub Pages settings and private security features were not fully available through the connected integration.
- No browser-based accessibility, rendering, print, or download test was executed during the baseline review.
- External textual resources named in the page are not hyperlinks, so link integrity could not be tested.
- Repository settings such as secret scanning, Dependabot alerts, and required status checks were not changed by this audit.
