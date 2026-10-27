# Community measurements

This directory stores aggregate observations, not follower lists or visitor identities.

The [preflight baseline](2026-10-27-preflight.json) comes from repository metadata read on 27 October 2026. It is not an installation count or a benchmark result. The connector's profile response did not expose a follower count, so that field is null rather than estimated from an old search snapshot.

## Definitions

- **Followers:** directly observed personal-account follower count. A difference is measurable only between two verified snapshots.
- **Stars / Forks / subscribers:** separate GitHub repository counts. `subscribers_count` is the watch/subscription count; `watchers_count` in repository metadata duplicates Stars and must not be substituted for subscribers.
- **Open issues and PRs:** GitHub's repository `open_issues_count` includes pull requests. Use a dedicated issue search to count issues alone.
- **Traffic:** available repository views, visitors and full clones are rolling-window measures. Preserve the window and retrieval date; never sum overlapping 14-day totals or daily unique visitors to claim unique people over a longer period. See [GitHub's traffic documentation](https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-traffic-to-a-repository).
- **First-run feedback:** a report of an attempted task. Distinguish a successful tool call and verified result from merely configuring a client.
- **External participants:** distinct human accounts participating in the relevant issues/PRs/discussions during the window, excluding maintainer accounts and bots. Do not count the same participant twice within a reported window.

Keep each snapshot's source and timestamp. Leave unavailable values null. Do not turn missing measurements into zeros. A change after publication is an observation, not proof of a causal growth effect.
