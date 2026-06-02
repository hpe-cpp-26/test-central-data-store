# test-central

A centralized test repository that aggregates documentation from multiple tools — GitHub, Confluence, and Jira — grouped by topic or project.

---

## Purpose

`test-central` is a **test data store** used for validating and experimenting with the project. It serves as a single location where related documents from different source tools are collected and organized together by topic, making it easier to work with cross-tool content in a unified way.

> **This is a test repository

---

## Repository Structure

```
root/
└── <group_name>/               
    ├── github/                 
    │   └── filename.md
    ├── confluence/             
    │   └── filename.md
    └── jira/
        └── filename.md
```

### Path Convention

```
<group_name>/<source_tool>/<filename>.md
```

| Segment | Description |
|---|---|
| `group_name` | The topic or project that ties the documents together |
| `source_tool` | The tool the document originated from (`github`, `confluence`, `jira`) |
| `filename.md` | The individual document |

---

## Source Tools

| Tool | Description |
|---|---|
| **GitHub** | Issues, pull requests, wikis, and other repo-level docs |
| **Confluence** | Pages and spaces exported from Confluence |
| **Jira** | Tickets, epics, and project documentation from Jira |

---

## Groups

Each top-level folder represents a group — a set of documents from different tools that all relate to the same topic or project. A single group may contain documents from one or more source tools.

---
