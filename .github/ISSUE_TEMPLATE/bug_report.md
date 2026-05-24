---
name: Bug report
description: Report an import, preprocessing, authentication, or item issue
title: "[Bug]: "
labels: [bug]
body:
  - type: input
    id: zabbix-version
    attributes:
      label: Zabbix version
      placeholder: "7.4.x"
    validations:
      required: true
  - type: input
    id: shelly-model
    attributes:
      label: Shelly model and firmware
      placeholder: "Shelly 2PM Gen4, firmware x.y.z"
    validations:
      required: true
  - type: dropdown
    id: mode
    attributes:
      label: Device mode
      options:
        - Switch mode
        - Cover / door / blind mode
        - Not sure
    validations:
      required: true
  - type: textarea
    id: problem
    attributes:
      label: What happened?
      placeholder: "Paste the Zabbix error or preprocessing message here. Remove passwords or private data."
    validations:
      required: true
