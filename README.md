# GitHub API Testing Practice

A Postman test suite built against the real, live GitHub REST API, practicing
authentication, full CRUD, rate limits, and pagination on a production system.

## What it covers
- Authentication with a Personal Access Token, including a negative test
  (request correctly rejected without a token)
- Full CRUD lifecycle on a real resource: create a repository, verify it
  exists, delete it, then verify the deletion (404 confirms cleanup)
- Rate limit checking via response headers (X-RateLimit-Limit,
  X-RateLimit-Remaining)
- Pagination testing (per_page, and verifying the Link header for next/prev
  pages)

## Setup
1. Generate your own GitHub Personal Access Token:
   - Classic token: Settings → Developer settings → Personal access tokens →
     Tokens (classic) → Generate new token → tick the `repo` scope
2. Open `GitHub.postman_environment.json` and paste your token in place of
   `PASTE_YOUR_OWN_TOKEN_HERE` for both `github_token` and
   `github_token_classic`
3. Import both files into Postman (or run directly with Newman)

## How to run it
newman run "GitHub API Testing.postman_collection.json" -e "GitHub.postman_environment.json"

## A note on security
This project intentionally ships with no real credentials. Real tokens
should never be committed to a public repository, this collection uses
environment variables so each user supplies their own.

## Skills demonstrated
Real API authentication testing, full CRUD lifecycle testing with cleanup,
response header assertions, rate limit verification, pagination testing,
and safe handling of credentials in a shared/public test suite.
