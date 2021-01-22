---
name: BIG-IQ AS3 Template Request
about: Request a new template to be added in the Community section
title: New Template [name]
labels: template
assignees: ''

---

<!--
Github Issues are consistently monitored by F5 staff, but should be considered
as best effort only and you should not expect to receive the same level of
response as provided by F5 Support. Please open a case
(https://support.f5.com/csp/article/K2633) with F5 if this is a critical issue.
-->

### Environment
 * Application Services (AS3) Version:
 * BIG-IQ Version:
 * BIG-IP Version:

### Summary
A clear and concise description of what this template does.

### BIG-IQ AS3 Template
1. Submit the following template:
```json
{
    "type": "object",
    "required": [
        "class"
    ],
    "properties": {
        "class": {
            "type": "string",
            "const": "Application"
        },
        "label": {},
        "remark": {},
        "template": {},
        "schemaOverlay": {}
    },
...
}
```
