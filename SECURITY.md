# Security policy

## Supported version

Security review applies to the current `main` branch and the published GitHub Pages site.

## Reporting a vulnerability

Do not disclose exploitable details in a public issue. Contact the repository owner privately through an agreed private channel. Include:

- affected file or URL;
- reproducible steps;
- impact and prerequisites;
- suggested mitigation, if known.

Do not include credentials, personal data, or live exploit payloads. The owner should acknowledge the report, assess severity, preserve evidence, and publish a remediation only after validation.

## Change controls

Security fixes must be developed on a separate branch and reviewed before merge. Direct pushes to `main`, force-pushes, history rewriting, unpinned third-party GitHub Actions, and unnecessarily broad workflow permissions are not acceptable.
