---
layout: post
title:  "Making a simple webpage and CMS for kids using Google Docs"
date:   2023-1-10 12:00:00 -0600
categories: web
---

# Overview
My 7 year old expressed interest in having his own web page, and I wanted a solution that he could interact with via his heavily secured school iPad.

The result was https://brooks.cool

# Steps

* Create a Google Doc using kid's Google account
* Share document to parent as Editor
* Set up notifications to alert you of changes
* Publish as iframe
* Embed iframe using a static webpage via Github Pages
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
	<iframe width="100%"
		src="https://docs.google.com/document/d/e/2PACX-1vSByy36Nn1OeX99y-XJ2atLcb90ktoLwSW31gL_zXC9VwgvC0z6FQxcJdh6aZQOMw8x5vyByDfWPjCo/pub?embedded=true"></iframe>
</body>

</html>
```
* If you'd like a custom domain (and not YOUR_USERNAME.github.io), set up DNS to point at the Github Pages instance.
	* This is pretty straightforward with Cloudflare.
