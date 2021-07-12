---
id: cz7_eAnC3jsWQ-7iTph9E
title: Personal Webpage
desc: ""
updated: 1626045349074
created: 1626034617083
---

## Inspiration

https://iuri.is/

## dev

```html
html, body { margin: 0; height: 100%; }
```

## Hosting

Amazon s3

[Configuring a static website using a custom domain registered with Route 53 - Amazon Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/userguide/website-hosting-custom-domain-walkthrough.html)
[Setting permissions for website access - Amazon Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteAccessPermissionsReqd.html)

### upload

https://gist.github.com/jlouros/9abc14239b0d9d8947a3345b99c4ebcb

```bash
aws s3 sync public s3://bucket_name.com && npm run s3:permissions
aws s3api put-object-acl --bucket bucket_name.com --key index.html --acl public-read
```

### Interesting

https://pierre.io/
https://jacekjeznach.com/
[microsoft/vscode](https://github.com/microsoft/vscode/blob/main/extensions/theme-defaults/themes/dark_vs.json)
[Align an element to bottom with flexbox](https://stackoverflow.com/questions/31000885/align-an-element-to-bottom-with-flexbox)
[how to remove the white space between two span tags?](https://stackoverflow.com/questions/39570556/how-to-remove-the-white-space-between-two-span-tags/39570687)
[Make <body> fill entire screen?](https://stackoverflow.com/questions/5721904/make-body-fill-entire-screen)
[A Complete Guide to Dark Mode on the Web](https://css-tricks.com/a-complete-guide-to-dark-mode-on-the-web/)
[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
[Google Fonts  |  Google Developers](https://developers.google.com/fonts)
https://fonts.google.com/specimen/Roboto+Slab?query=robot&preview.text=gustavo.hello()&preview.text_type=custom#about
[Browse thousands of Developer images for design inspiration | Dribbble](https://dribbble.com/search/developer)
[put-object — AWS CLI 2.2.18 Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3api/put-object.html)
