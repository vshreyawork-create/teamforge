PS1 · Race-proof team formation at scale
Hundreds of people clicking "join" at the same second. Exactly one gets the last seat.

Your task: Build a production-grade team-formation service for a hackathon with 10,000 participants: teams with invite codes, join requests the leader accepts or declines, and a live "looking for teammates" board. It must stay correct when hundreds of people click at the same moment.

Must have:

Rules: team size between a minimum and a maximum, one team per person per hackathon, invite codes that expire, leadership passes on when the leader leaves, the last member leaving deletes the team
Race-proof: 50 people try to take the last seat in a team at the same instant and exactly one gets it. Prove it with an automated concurrency test
Idempotent: a retried request (double click, flaky network) never joins twice or creates two teams
Real-time: the board and team pages update live for everyone (WebSockets or server-sent events), no refresh
Secure: authentication, only the leader can accept, decline or remove; invite codes cannot be brute-forced (rate limits, enough entropy); every input validated
An audit log of every team change: who, what, when
Teammate suggestions: an endpoint that ranks people by complementary skills and time zone, with the scoring explained
Tested and fast: at least 20 API tests, including the race test, running in CI (GitHub Actions). A seed script for 10,000 users and 2,000 teams, and a load test (k6 or autocannon) showing p95 under 200 ms on the board endpoint with 100 concurrent users
A React UI for the whole flow that works on a phone and with a keyboard only
Deployed: a live URL on any free tier
Bonus: optimistic UI with rollback on conflict, Docker Compose for one-command setup, tracing or metrics, a chaos test (kill the server mid-join and show nothing is corrupted).

Submit: GitHub repo, live URL, the load-test report, and a 1-page design doc: data model, how you prevent races, the trade-offs you made and what you would do with one more week, plus a walkthrough video of up to 5 minutes.

What we look at: Correctness under concurrency first, then your design decisions and how well you defend them, then code quality, tests and UX.
