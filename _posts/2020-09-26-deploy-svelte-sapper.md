---
title: 'Deploy a Svelte / Sapper application'
description: 'Deploy Svelte'
date: 2020-09-26T01:41:48+00:00
created: 2020-09-26T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'svelte'
color: '#7AAB13'
permalink: /svelte-sapper-deploy
categories:
  - Angular
tags:
  - Angular, Svelte

introduction: 'Deploy a Svelte / Sapper application'
---

### Svelte / Sapper deploy

I started to play with Svelte / Sapper as an alternative to Angular.

The development of a simple application is quick and intuitive, I had issues to deploy a small application easily in the cloud.

The solution I found is to create a Docker image of the application and deploy it using Jelastic.

Being the content quite static I exported the result of the original REST answers of the Java backend in JSON files.  

The website is visible here: [java-version.com](https://java-version.com)

_Dockerfile_
```dockerfile
FROM node:14-alpine

WORKDIR /usr/src/app
# the entire project is copied
COPY / ./
RUN npm install
RUN npm run build

CMD ["node", "__sapper__/build"]

EXPOSE 3000

ENV HOST=0.0.0.0
```

In Jelastic:
<img src="/assets/img/uploads/2020/2020-09-26_jelastic.gif" alt=""/>


I deployed the image behind a NGINX Load Balancer.

### Issues

*Configuration*

The main issue for me was the configuration of different environments: development and 'production'.
In Angular and Java every environment has his own configuration file out of the box.

I didn't find this in Sapper. The solution was to use external plugins. Even changing the port of the server required searching a solution on GitHub (prefix with PORT 80 the starting instruction was the easiest).

Working with different environments and services (backend etc.) it's annoying to don't have a pre-defined solution.

*TypeScript*

I tried to convert my project in TypeScript, Svelte provides an 'easy migration'. I think the migration failed with Sapper.
I ended using only JavaScript. This is not a blocker for a small project, different story for a big enterprise solution with many developers.

### Personal Opinion

I like Svelte a lot. The main project comes with some companion solution for SSR and static website generation that fill some missing features of Angular.
The compilation central idea is a true alternative to React/Vue/Angular. Unfortunately Svelte doesn't seem to receive a lot of interest in the enterprises.



