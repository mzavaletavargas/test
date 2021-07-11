---
id: rJkjiic8vrzBrDbRGWpFv
title: Static Website
desc: ""
updated: 1626029904098
created: 1626029750653
---

# Static Website using S3

Clear all **Block public access (bucket settings)**

Sync folder with S3 static server

```bash
aws s3 sync docs s3://static.gustavozavaleta.com
```

Give public access where needed

```bash
aws s3 sync docs s3://static.gustavozavaleta.com
```
