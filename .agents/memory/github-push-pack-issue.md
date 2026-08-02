---
name: GitHub push pack issue
description: A repository can pass local Git verification yet fail GitHub unpacking because of a problematic historical pack.
---

When GitHub rejects a push with “did not receive expected object” or “remote unpack failed” after authentication succeeds, publish a clean archive of the current checked-out tree from a temporary repository rather than repeatedly retrying the original history.

**Why:** The original local pack can be internally readable while still producing an incomplete or incompatible transfer pack for GitHub.

**How to apply:** Keep the user’s working tree and branch unchanged; initialize the temporary repository from `git archive HEAD`, push its new commit, and clearly disclose that the published repository has a clean initial history.