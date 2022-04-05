---
layout: post
current: post
cover:  assets/images/github-pages-with-strato/github-pages.jpg
navigation: True
title: GitHub Pages with Custom Domain from Strato
date: 2022-04-04 06:00:00
tags: [Webdevelopment, Strato]
class: post-template
subclass: 'post'
author: ghost
---

# How to get GitHub Pages work with a custom domain from strato?

When I was trying to configure the domain for this blog here I got stuck while setting up a custom domain in Github Pages. The solution is not straight forward and thats why I described it here for you. The needed configuration is specific for strato (webhosting provider) but may apply to other providers as well.

## Configuration on GitHub
- "GitHub Repository Project" --> Settings --> Pages

## Configuration on strato
- add subdomain with www.yourdomain.com
- configure A-Record for the subdomain
- configure AAAA-Record for the subdomain

!!! It will stuck when the www. subdomain configuration is missing !!!


### Documentation from GitHub:
-  

### Helpful post:
- [Certificate request error is persistent (TLS Certificate can’t be provisioned)](https://github.community/t/certificate-request-error-is-persistent-tls-certificate-cant-be-provisioned/11008/16)
