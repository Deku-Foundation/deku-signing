# Deku Signing and Repository Trust Model

Status: proposed model; no production key or signing service exists.

## Goals
Authenticate repository metadata and release artifacts, detect rollback/freeze attacks where practical, support key rotation and revocation, and keep signing authority separate from builds.

## Proposed trust objects
- Root trust metadata: trusted key identities, threshold/role policy, expiry and rotation.
- Repository snapshot/targets metadata: package names, versions, architectures, artifact digests and signed freshness information.
- Release manifest: ISO digest, source commit, profile revision, build provenance, SBOM and acceptance-test evidence.
- Transparency/audit record: append-only publication event where feasible.

Evaluate established update-framework designs such as TUF rather than inventing a new cryptographic protocol. Select formats and libraries only after threat-model and maintenance review.

## Key rules
- Private keys never enter Git, ISO images, build workers or PR workflows.
- Separate root/metadata roles from routine release signing.
- Document offline backup, rotation, expiry, revocation and compromise response before first trusted repository.
- A SHA-256 checksum alone does not authenticate the publisher.
- Do not claim signatures are active until CI verifies real signed metadata end-to-end.
