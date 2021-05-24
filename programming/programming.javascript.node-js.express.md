---
id: 4df19af7-cb3d-4fbc-a1b1-fafa17b9bffd
title: Express
desc: ""
updated: 1621707441948
created: 1621707420735
---

## Create a static server

```javascript
express.static(root, [options]);
```

```javascript
app.use(express.static("public"));
```

```javascript
router.get("/", function (req, res) {
  res.sendFile(path.join(__dirname + "/index.html"));
  //__dirname : It will resolve to your project folder.
});
```

## Aditional Information

- https://expressjs.com/en/starter/static-files.html
- https://codeforgeek.com/2019/03/render-html-file-expressjs/
