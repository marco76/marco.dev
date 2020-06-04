---
title: 'Time validation pattern for Angular / Javascript'
description: 'RegExp for time validation'
date: 2020-05-29T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'angular'
color: '#7AAB13'
permalink: /angular-time-validation-pattern
categories:
  - Angular, javascript
tags:
  - Angular

introduction: 'Time validation RegExp pattern'
---
# Time validator in Angular and Javascript

We want to validate an input, the required format is _hh:mm_

Examples:

8:59 AM = 08:59

8:59 PM = 20:59

## Javascript regular expression
```javascript
/^(0[0-9]|1[0-9]|2[0-3]):[0-5][0-9]$/
```

## Angular form

```typescript
formControl = new FormControl('',
 Validators.pattern(/^(0[0-9]|1[0-9]|2[0-3]):[0-5][0-9]$/));
```

Notice that we are not using a string but a [JS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)/TS RegExp