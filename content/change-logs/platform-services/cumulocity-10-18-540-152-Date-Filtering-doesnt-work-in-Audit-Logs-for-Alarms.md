---

date: 2024-07-12
title: Audit logs for repeating alarms are created with the date of the last alarm update
product_area: Platform services
change_type:
  - value: change-VSkj2iV9m
    label: Fix
component:
  - value: component-OG_650_b2
    label: Core platform
build_artifact:
  - value: tc-QHwMfWtBk7
    label: cumulocity
ticket: MTM-58098
version: 10.18.540.152
---

Audit logs for repeating alarms used the alarm creation date which resulted in audit logs having past dates. This issue has been fixed and now audit logs for repeating alarms are created with the date of the last alarm update.