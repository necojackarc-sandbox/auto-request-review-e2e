# auto-request-review e2e sandbox

Scratch repo for manually exercising the `require-review:` comment
directive added in necojackarc/auto-request-review#159 (issue #130).

## Manual test steps

1. Open a PR against `main`.
2. Confirm the `Auto Request Review` check runs and passes (no
   `require-review` directive posted yet).
3. Post a PR comment: `require-review: @<some-collaborator>`.
4. Confirm the check now fails with "Missing required approving
   review(s) from: <some-collaborator>".
5. Have `<some-collaborator>` submit an approving review.
6. Confirm the check re-runs (via the `pull_request_review` trigger)
   and now passes.
7. Post `require-review: @<some-collaborator>` from an account
   *without* write access to this repo and confirm it's ignored (check
   stays green, and the Action log shows "Ignoring ... insufficient
   permission").
