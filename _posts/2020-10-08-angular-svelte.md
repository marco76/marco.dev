---
title: 'Angular and Svelte: Test drive'
description: 'Differences between Angular and Svelte'
date: 2020-10-08T01:41:48+00:00
created: 2020-10-08T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'svelte'
color: '#7AAB13'
permalink: /svelte-angular-differences
categories:
  - Angular
tags:
  - Angular, Svelte

introduction: 'Angular and Svelte some differences'
---

### Why this 'Test'
*work in progress, this page will be updated when more information will be available*

I'm developing 2 personal websites to publish on the web and I have to improve their SEO.

One website is about Angular [https://ngpef.com](https://ngperf.com) and I'm using Angular as framework.

The second website is about Java and I'm using Svelte and Sapper to build it: [https://java-version.com](https://java-version.com).

The goal is to evaluate the advantages and issues that I have with these technologies, the two frameworks are different with different targets and is not my interest declare that one is better than the other.

### Differences

|*Task*|*Angular*|*Svelte*|
|Deploy on the web|Easy peasy: Netlify|Some issues, final solution: Docker in Jelastic |
|Different properties per environment|Out of the box|hmmm ... still looking the best solution|
|Static website|Angular Universal ... never worked for me|Sapper, worked well|
|Components|Material, Bootstrap, ...|DIY (Do it yourself)|
|Performances (Google Lighthouse)|96 (Excellent)| 99 (Excellent)|
|TypeScript|Default|Recently added, didn't work for my project (Sapper)|
|Startup|ng new [project-name]|clone a template|
|Add some meta to head|use `import {Meta, MetaDefinition} from '@angular/platform-browser';` + 4-5 lines of code|easy: `<svelte:head><meta name="Description" content="List..."</svelte:head>">`
|Documentation|Extensive and required|I didn't use a lot (intuitive)|                                                                                                                       		`|

