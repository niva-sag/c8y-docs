---
date: 2024-03-28
title: Improved performance of activating or deactivating smart rules for multiple devices
change_type:
  - value: change-VSkj2iV9m
    label: Fix
product_area: Platform services
component:
  - value: component-0UgqXH1Ys
    label: Administration
build_artifact:
  - value: tc-pjJiURv9Y
    label: ui-c8y
ticket: MTM-49732
version: 10.18.292.0
---

The performance of activating or deactivating a smart rule for multiple child assets has been improved by executing only a single request instead of multiple requests.