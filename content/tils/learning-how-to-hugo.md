---
title: TIL how to use Hugo
date: 2023-02-02T14:53:23.376Z
tags:
  - go
  - hugo
  - digital ocean
slug: til-hugo
lastmod: 2023-02-03T23:38:15.781Z
---
TIL how to use [Hugo](https://gohugo.io/) to publish this blog! Hugo is a static site generator written in `Go`. It can seem a bit intimidating at first, but I found if you stay within it's rails it's really quite a nice static site generator.

I am also hosting this for free using [Digital Ocean's App Platform free tier](https://www.digitalocean.com/pricing/app-platform). Basically they let you run up to 3 static sites totally for free using their app platform.

It is especially easy to use in combination with Hugo as the app platform does some special "guessing" to determine how to automatically build your site using these things called build packs.

Here's some helpful resources for running a Hugo site on DO.

- [How To Build and Deploy a Hugo Site to DigitalOcean App Platform](https://www.digitalocean.com/community/tutorials/how-to-build-and-deploy-a-hugo-site-to-digitalocean-app-platform)
- [Digital Ocean Hugo Buildpack](https://docs.digitalocean.com/products/app-platform/reference/buildpacks/hugo/)

However one tricky thing about the build pack auto-detection I ran into is that it can be too smart for its own good.

For example, the Hugo theme I'm using, [Congo](https://github.com/jpanther/congo), recommends using the `Hugo Module` approach to install the theme, rather then the `git submodule` method. But if you use the `Hugo Module` approach then DO will think your app is a generic `Go` app, as the generic `Go` build pack looks for things like a `go.mod` or `go.sum` file and the `Hugo Module` approach creates those files.

The `Hugo` build pack is just looking for a `config.toml` file, and it seems like the genereic `Go` build pack clashes with it. The solution was to just use the plain ole `git submodule` method for `Hugo` themes. This allowed the `Hugo` build pack to be correctly selected.

Basically when following the app platform instructions, you want to see this build pack.

![Alt text](hugo-buildpack.jpg "Image caption")

Anyways, I'm excited to finally have my little pesonal slice of the web!

#### Click the referral banner below to get $200 in credit over 60 days.
 [![DigitalOcean Referral Badge](https://web-platforms.sfo2.digitaloceanspaces.com/WWW/Badge%202.svg)](https://www.digitalocean.com/?refcode=681bf6988ee7&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)
