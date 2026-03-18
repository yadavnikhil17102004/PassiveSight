# Contributing to TRACEGUARD AI™ Community Edition

Thank you for your interest in TRACEGUARD AI™ Community Edition.

This project is **source-visible but proprietary**. To protect the integrity of the software and future commercial editions, we do **not accept outside contributions**.

## Guidelines

- Do not submit pull requests or patches.
- Do not fork the repository for competing products.
- Do not redistribute modified versions of the Software.

## Contact

For questions, business inquiries, or information about commercial/professional editions, please contact:

[REDACTED_EMAIL]

## Maintainer Validation

For internal testing and release QA, validate Azure `.env` settings before manual Burp testing:

```bash
./tools/test_azure_env.sh ./.env
```

Expected result: `STATUS: VALID`.

