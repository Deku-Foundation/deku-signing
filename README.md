# Deku Signing and Trust

Defines trust policy for package and release metadata, signatures, key rotation and verification.

## Status

Design/bootstrap stage. No production keys, signing service or trusted package repository exists.

## Responsibilities

- Specify repository metadata signatures, release artifact signatures, key identity, rotation, expiration and revocation.
- Separate signing approval from source builds and untrusted pull-request workflows.
- Define offline recovery and incident response for a compromised key.
- Use established cryptographic formats and reviewed libraries; never invent cryptography.

## Security rules

Never commit private keys, recovery material or production credentials. A digest alone is not publisher authentication. Keep actual keys in an appropriate external signing system; this repository should contain policy and public verification material only.
