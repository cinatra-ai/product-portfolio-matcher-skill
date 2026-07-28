# Cinatra Product Portfolio Matcher

The classification rules Cinatra applies when it has to decide whether an uploaded file is a product-portfolio or product-line description. It is the knowledge half of `@cinatra-ai/product-portfolio-artifact`, packaged as its own skill so the artifact extension declares a dependency on it instead of shipping it inside.

**Install:** Install `@cinatra-ai/product-portfolio-matcher-skill` in your Cinatra instance. `@cinatra-ai/product-portfolio-artifact` installs it automatically as a declared dependency.

**Usage:** The classifier worker loads this skill through the artifact extension's declared `matcher` dependency edge — you do not invoke it directly. It reads the attached file plus the recorded upload signals and answers with a match verdict, a confidence score and a short rationale.

**Configuration:** None. The skill carries no credentials and reads no settings; the host supplies the model runtime.

**Development:** Clone the repository and run `node extension-kind-gate.mjs --package-root .` to validate the manifest. The bundle lives in `skills/product-portfolio-matcher/` — a single `SKILL.md` router with no reference files.

**Troubleshooting:** If uploads are never typed as Product Portfolio, check that `@cinatra-ai/product-portfolio-artifact` is installed and that its declared dependency on this package resolved; an unresolved edge means the classifier has no rules to apply and the upload keeps its structural identity.

## Works with

- Cinatra Product Portfolio artifact extension
- Any extension declaring a skill dependency on this package

## Capabilities

- Decide whether an attached file is a product-portfolio or product-line description
- Name the look-alike document kinds that must NOT match
- Return a calibrated confidence score the host compares against the extension's threshold
- Answer as strict JSON with no surrounding prose
