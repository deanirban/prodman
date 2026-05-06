# SSO Token Lifetime Policy Controls

## Overview
Allow account administrators to configure SSO session token lifetimes and idle-timeout policies per organization, with optional overrides for high-risk roles.

## Goals
- Per-org configurable access-token TTL (15min–24h)
- Idle timeout enforcement across all GreenLake services
- Audit log of policy changes with actor and reason

## Success Criteria
- Policies enforced uniformly across all SSO-protected services
- Zero session-stickiness regressions reported in first 30 days
