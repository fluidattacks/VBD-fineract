# VBD-fineract: synthetic vulnerability benchmark

This fork is a **synthetic, openly labelled benchmark**. It is not the upstream project
and must not be used as one. Each sample is an isolated pair of branches off `baseline`:

- `baseline`: the pinned upstream commit plus any hardening; the common ancestor.
- `smpl/<NNN>/safe`: the genuine negative (validated control) of sample `NNN`.
- `smpl/<NNN>/vuln`: `safe` plus exactly one commit that weakens the control.

The class and the coordinates of every sample live only in `GROUND_TRUTH.csv` on this
orphan branch, never in the analysed branches.

| sample | file | class |
|---|---|---|
| 001 | `fineract-security/src/main/java/org/apache/fineract/infrastructure/security/filter/TwoFactorAuthenticationFilter.java` | F115 Security controls bypass or absence |
| 002 | `fineract-core/src/main/java/org/apache/fineract/infrastructure/instancemode/filter/FineractInstanceModeApiFilter.java` | F115 Security controls bypass or absence |
| 003 | `fineract-loan/src/main/java/org/apache/fineract/portfolio/delinquency/api/DelinquencyApiResource.java` | F115 Security controls bypass or absence |
| 004 | `fineract-provider/src/main/java/org/apache/fineract/infrastructure/security/service/TwoFactorServiceImpl.java` | F115 Security controls bypass or absence |
| 005 | `fineract-document/src/main/java/org/apache/fineract/infrastructure/contentstore/util/DefaultContentPathSanitizer.java` | F115 Security controls bypass or absence |
| 006 | `fineract-core/src/main/java/org/apache/fineract/commands/service/CommandSourceService.java` | F115 Security controls bypass or absence |
