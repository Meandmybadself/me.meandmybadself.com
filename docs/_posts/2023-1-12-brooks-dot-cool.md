---
layout: post
title:  "Simple webpage & CMS using Google Docs"
date:   2023-1-10 12:00:00 -0600
categories: web
---

# Overview
My 7 year old expressed interest in having his own web page, and I wanted a solution that he could update using his heavily secured school iPad.

The result was https://brooks.cool

# Steps

* Create a Google Doc using kid's Google account [https://doc.new](https://doc.new)
* If you'd like some level of oversight:
	* Share the document to yourself parent as Editor (`File > Share > Share with Others`)
	* Set up notifications to alert you of changes

|----|-----|
|<img src='/assets/brooks-dot-cool/notifications.jpg' width='400' alt=''/>|<img src='/assets/brooks-dot-cool/notifications-menu.jpg' width='400' alt=''/>|


* Publish the document as iframe (`File > Share > Publish to Web`)
	* Click `Embed` and copy the iframe HTML.
<img src='/assets/brooks-dot-cool/embed.jpg' width='400' />

* [Create a new Github Pages static page](https://github.com/Meandmybadself/simple-github-site/generate).
* Edit index.html, replacing the iframe with the one you copied from Google Docs.

```
<html>

<head>
	<title>Brooks Dot Cool</title>
	<style>
		html,
		body {
			width: 100%;
			height: 100%;
			margin: 0;
			padding: 0;
			display: flex;
			flex-direction: column;
			align-items: center;
		}

		iframe {
			max-width: 468pt;
			margin: 0 auto;
			height: 100%;
			margin: 0;
			padding: 0;
			border: 0;
		}
	</style>
</head>

<body>
	<!--- Replace the line below //-->
	<iframe width="100%"
		src="https://docs.google.com/document/d/e/2PACX-1vSByy36Nn1OeX99y-XJ2atLcb90ktoLwSW31gL_zXC9VwgvC0z6FQxcJdh6aZQOMw8x5vyByDfWPjCo/pub?embedded=true"></iframe>
</body>

</html>
```

* If you'd like a custom domain (and not YOUR_USERNAME.github.io), [use these instructions](https://blog.cloudflare.com/secure-and-fast-github-pages-with-cloudflare/).
