---
title: 'Angular quick notes'
description: 'FAQ'
date: 2020-02-22T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'angular'
color: '#7AAB13'
permalink: /angular-quick-notes
categories:
  - Angular
  - Angular Material
  - JavaScript
tags:
  - Angular
  - Angular Material
  - JavaScript

introduction: 'Angular and JavaScript FAQ'
---

## FAQ

I regularly look for solutions to the following problems. For this reason I collected here questions and answers.
There is no logic in the order and the solution is more a quick note than a full article, if many questions are about the same subject I will create a separate page.

You are welcome to add questions / answers in the comments.


## Node.js: I need multiple versions of Node.js installed on my machine ...
Use [nvm](https://github.com/nvm-sh/nvm)

If you are using MacOS, https://formulae.brew.sh/formula/nvm:
`
brew install nvm
`
If you are using `zsh` (MacOS 15.x) you have to update `.zshrc` according to the documentation of Homebrew.

_Commands_
- Install the latest node version: `nvm install node`
- Use the latest node version: `nvm use node`
- Install the latest LTS version: `nvm install --lts`
- Install a specific version (e.g.): `nvm install 10.10`

List of node.js releases:
https://nodejs.org/en/download/releases/

### NgRX: Can I Dispatch an event inside a reducer? How can I subscribe an action?
It should be avoided, this is an antipattern: https://stackoverflow.com/questions/36730793/can-i-dispatch-an-action-in-reducer

In my case the question come often because when I need to chain the events the 'shortcut' would be to start them in the reducer and not in the business code.

Example solution, in this case after an event occurred I want to load some data from the store and call a new action with this data:
```javascript
constructor(public actions$: Actions, public store: Store<AppState>) {

const observableOfTheEventToStart$ )  store.select(state => state.yourState);

actions$.pipe(
    ofType(YourActions.ActionSuccess),
    mergeMap(() => observableOfTheEventToStart$),
    map(resultEventToStart => this.store.dispatch(new SeconfActionToCall(resultEventToStart)))
).subscribe();

}
```

## Drag Drop and Shift
This is usually used in tree structures / catalogs

```javascript
insertAndShift(originalArray, fromIndex, toIndex) {
    const cutFrom = originalArray.splice(fromIndex, 1)[0];
    originalArray.splice(toIndex, 0, cutFrom);
 }
```


