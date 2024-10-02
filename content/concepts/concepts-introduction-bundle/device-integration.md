---
weight: 10
title: Device Integration
---

{{< product-c8y-iot >}} offers multiple methods for connecting your equipment:

- Pre-integrated IoT gateways: Choose from [certified devices](https://ecosystem.{{< domain-c8y >}}/device-ecosystem/) offered by our partners for the easiest integration.
    
- thin-edge.io: [thin-edge.io](https://thin-edge.io/) is recommended for custom device integration. Follow the [Getting started with thin-edge.io](/device-integration/device-integration-thin-edge/) tutorial for a hands-on example.
    
- Direct integration: Connect devices via [HTTP REST](/device-integration/device-integration-rest/) or [MQTT](/device-integration/mqtt) interfaces. MQTT interfaces are designed for minimal device-side logic, suitable for microcontroller-based devices.
    
- LPWAN support: Native [LwM2M support](/protocol-integration/lwm2m/) and [LoRa Network Server integration](/protocol-integration/lora-loriot/) for Low-Power-Wide-Area-Network devices.