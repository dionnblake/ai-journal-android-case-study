# Privacy and Security Notes

This app handles sensitive personal reflection data. The public showcase is designed around that reality.

## Data sensitivity

Journal entries can contain personal, emotional, business, and strategic information. Treating entries as sensitive data shaped these decisions:

- local-first storage
- no real journal entries in screenshots
- no source code in public showcase
- no prompt templates or AI orchestration details in public docs
- no broad third-party repository access

## API keys

The private app supports user-configured AI provider keys. Public documentation does not include real keys, local config, or provider account details.

Safe pattern:

- local development keys stay in ignored local files or app settings
- runtime key state lives in preferences
- public repo contains no secrets

## Public showcase rules

Allowed:

- architecture diagrams
- product screenshots with fake or empty data
- system-design notes
- high-level tech stack
- demo video with redacted content

Not allowed:

- source code
- proprietary prompt chains
- monetization logic
- real journal content
- private API keys
- private roadmap or business logic

## Recruiter access model

Default path:

1. Public case study for first review
2. Demo video for product proof
3. Sanitized code sample for code quality
4. Guided private code walkthrough only for serious technical interviews

Do not grant public or broad collaborator access to the private repository. GitHub view access can still be cloned or copied.
