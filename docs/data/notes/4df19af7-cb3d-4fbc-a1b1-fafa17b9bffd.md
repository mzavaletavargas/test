
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
