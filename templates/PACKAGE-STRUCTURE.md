# Package Structure Template

Standard structure for creating new packages.
vertical-name/
│
├── README.md
│   └── Vertical documentation
│
├── CHANGELOG.md
│   └── Version history
│
├── packages/
    ├── [vertical-name]-pt-br-v1.0.zip
    └── Portuguese package
    ├── [vertical-name]-es-v1.0.zip
    └── Spanish package
│
└── assets/
│   ├── screenshots/
│   │    ├── 01-welcome.png
│   │    ├── 02-main-flow.png
│   │    ├── 03-xapp-form.png
│   │    └── 04-confirmation.png
│   ├── demo-scripts/
│   │     └── 01-welcome.png
│   ├── docs/
│       └── conversation-flows.md
│
├── demo-script.md
│   └── Presentation guide
│
└── docs/
    ├── use-cases.md
    ├── integration-guide.md
    └── troubleshooting.md

### What Goes Where

**Root level:** Main files (README, CHANGELOG, packages)

**assets/screenshots:** Images showing the demo

**assets/conversation-flows.md:** Conversation examples

**assets/demo-script.md:** How to present

**assets/docs/:** Detailed documentation

---

**Last Updated:** May 4, 2025