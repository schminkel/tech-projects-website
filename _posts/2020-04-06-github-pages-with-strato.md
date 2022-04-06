---
layout: post
current: post
cover:  assets/images/github-pages-with-strato/github-pages.jpg
navigation: True
title: GitHub Pages with Custom Domain from Strato
date: 2022-04-04 06:00:00
tags: [Webdevelopment]
class: post-template
subclass: 'post'
author: ghost
---

# How to get GitHub Pages work with a custom domain from strato?

When I was trying to configure the custom domain for my blog on GitHub I got stuck while setting it up via the Github Pages configuration. No error was show and the creation of SSL certificates displayed a progress that never finished. Finally I found a solution which is not straight forward and thats why I described it here for you. The needed configuration may be specific for strato [(www.strato.de)](http://www.strato.de) but may vary/apply to other domain providers as well.


## Configuration on GitHub
Go to the main page of your "GitHub Repository Project" --> "Settings" --> "Pages" and enter your custom domain (e.g. tech-projects.blog).

![Configuration on GitHub 1](/assets/images/github-pages-with-strato/2022-04-06_19-25-45.png)
*Settings Button on GitHub*

![Configuration on GitHub 2](/assets/images/github-pages-with-strato/2022-04-06_19-36-07.png)
*GitHub Pages Configuration on GitHub*

> BUT, this will not work without the correct configuration on the domain provider side!


## Configuration on Strato

### Domain configuration (e.g. tech-projects.blog)
- Configure the A-Record for your domain and add one of these IPs (IPv4).
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

- Configure the AAAA-Record for your domain and add one of these IPs (IPv6).
```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

### Sub-Domain configuration (e.g. www.tech-projects.blog)
- Add "www." subdomain for your domain.
- Configure the A-Record and add an IP for the subdomain as for the domain.
- Configure the AAAA-Record and add an IP for the subdomain as for the domain.

> Adding the "www." subdomain with an A-Record IP will do the trick here!

![Domainverwaltung Strato](/assets/images/github-pages-with-strato/2022-04-06_20-42-15.png)
*Domainverwaltung Strato*


## Documentation on GitHub
-  [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

## Helpful post
- [Certificate request error is persistent (TLS Certificate can’t be provisioned)](https://github.community/t/certificate-request-error-is-persistent-tls-certificate-cant-be-provisioned/11008/16)
