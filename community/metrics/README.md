# Community measurements

This directory stores aggregate observations, not follower lists or visitor identities.

## Verified baseline

The [first public-API snapshot](2026-10-27.json), recorded at **2026-10-27 16:22:33 UTC**, contains **5 personal followers** and TOMC's **265 Stars, 25 Forks and 28 subscribers**. These are baseline observations, not growth attributed to the new content. The [collection run](https://github.com/ZipengWu365/ZipengWu365/actions/runs/40540271783) completed successfully.

The earlier [preflight snapshot](2026-10-27-preflight.json) is retained unchanged. At that point the connector's profile response did not expose a follower count, so its field is null. The later workflow obtains public aggregate counts directly from GitHub's API; it does not read follower identities or private user data.

## Collection window

[The workflow](../../.github/workflows/community-metrics.yml) is configured for one daily public-count snapshot, with a nominal trigger at 17:23 UTC. Scheduled execution may be delayed. Its date guard allows data collection only from **27 October through 10 November 2026**, inclusive. Existing same-day snapshots are not overwritten.

A separate review task is scheduled for **3 November and 10 November**, in the London evening. The final review is instructed to remove the scheduled trigger while retaining manual dispatch. The date guard already prevents data collection outside the experiment window, even before that cleanup occurs. Existing TOMC traffic collection is unchanged.

## Definitions

- **Followers:** directly observed personal-account follower count. A difference is measurable only between two verified snapshots.
- **Stars / Forks / subscribers:** separate GitHub repository counts. `subscribers_count` is the watch/subscription count; `watchers_count` in repository metadata duplicates Stars and must not be substituted for subscribers.
- **Open issues and PRs:** GitHub's repository `open_issues_count` includes pull requests. Use a dedicated issue search to count issues alone.
- **Traffic:** available repository views, visitors and full clones are rolling-window measures. Preserve the window and retrieval date; never sum overlapping 14-day totals or daily unique visitors to claim unique people over a longer period. See [GitHub's traffic documentation](https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-traffic-to-a-repository).
- **First-run feedback:** a report of an attempted task. Distinguish a successful tool call and verified result from merely configuring a client.
- **External participants:** distinct human accounts participating in the relevant issues/PRs/discussions during the window, excluding maintainer accounts and bots. Do not count the same participant twice within a reported window.

Keep each snapshot's source and timestamp. Leave unavailable values null. Do not turn missing measurements into zeros. A change after publication is an observation, not proof of a causal growth effect.
