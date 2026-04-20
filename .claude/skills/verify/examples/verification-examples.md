# Verification Examples

## Bad verification claim

"This should be fixed now."

Why it is bad:

- no proof command
- no fresh output
- no evidence tied to the claim

## Good verification claim

"Ran `npm test -- tests/auth/session.test.ts` and it passed with 4/4 passing. Ran `npm run typecheck` and it exited 0. The session invalidation change is verified for the targeted regression and type safety."

## Honest incomplete verification

"Targeted tests passed, but I could not run the full build because the repo requires unavailable environment variables `FOO_API_KEY` and `BAR_URL`. The specific change is partially verified, but full build evidence is still missing."
