# Air-Gapped Telemetry Export Pipeline

## Overview
Provide an offline-capable telemetry export pipeline so on-prem GreenLake deployments in air-gapped environments can periodically push aggregated, anonymized usage data via removable media or scheduled batch transfer.

## Goals
- Define a portable, signed export bundle format
- Schedule and queue exports without internet access
- Support manual review and approval before bundle release

## Success Criteria
- Bundle creation succeeds for clusters of 200+ hosts in under 10 minutes
- Cryptographic signing on every bundle, verified on import
