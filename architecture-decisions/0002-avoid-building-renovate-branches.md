# 2. Avoid building renovate branches

Date: 2020-11-16

## Status

Accepted

## Context

In order for renovate PR branches to be built in isolation, they could be
included in the list under the `push` trigger in the test workflow as
`renovate/**`. However, that would result in duplication for the builds
triggered by the PR being opened or updated.

These two build types are intended to catch differing problems between the
isolated branch vs the branch merged with the mainline. However, as short-lived
as the renovate PRs are intended to be, it should be rare that the results of
the two builds are different.

## Decision

We will not build the renovate branches as part of the test workflows.

## Consequences

Redundant builds will be avoided and we will rely on the PR builds to verify
that the dependency updates are safe to merge.
