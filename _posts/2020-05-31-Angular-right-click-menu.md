---
title: 'Right click context menu with Angular'
description: 'Menu for dynamic lists and tables'
date: 2020-05-31T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'angular'
color: '#7AAB13'
permalink: /angular-right-click-menu
categories:
  - Angular
  - Angular Material
tags:
  - Angular
  - Angular Material

introduction: 'Right click custom menu inside dynamic lists with Angular Material'
---

## Create a right click context menu inside a dynamic list or table

[GitHub demo](https://github.com/marco76/angular-right-click-menu)
<img src="/assets/img/uploads/2020/blog-right-click.gif" alt="" style="width: 25%; height:25%"/>

In this use case, we need to link each element of a list or table to a right-click context [mat-menu](https://material.angular.io/components/menu/overview).
To solve the problem we need to dynamically create the menu after each click.

### Component code

Here is important to notice that we define the position of the menu using the coordinates of the mouse.

```typescript
// we create an object that contains coordinates
  menuTopLeftPosition =  {x: '0', y: '0'}

  // reference to the MatMenuTrigger in the DOM
  @ViewChild(MatMenuTrigger, {static: true}) matMenuTrigger: MatMenuTrigger;

  /**
   * Method called when the user click with the right button
   * @param event MouseEvent, it contains the coordinates
   * @param item Our data contained in the row of the table
   */
  onRightClick(event: MouseEvent, item) {
      // preventDefault avoids to show the visualization of the right-click menu of the browser
      event.preventDefault();

      // we record the mouse position in our object
      this.menuTopLeftPosition.x = event.clientX + 'px';
      this.menuTopLeftPosition.y = event.clientY + 'px';

      // we open the menu
      // we pass to the menu the information about our object
      this.matMenuTrigger.menuData = {item: item}

      // we open the menu
      this.matMenuTrigger.openMenu();

  }
```

## html code


```html
<!-- we generate a number of items dinamically-->
<div *ngFor="let i of getExamples(20)">
  <!-- when the user clicks on the div the onRightClick event is called, we pass a simple object-->
  <div (contextmenu)="onRightClick($event, {content: 'Item ' + i})"
  style="padding-bottom: 20px;">
    Item {% raw %}{{i}}{% endraw %}
  </div>
</div>

<!-- an hidden div is created to set the position of appearance of the menu-->
<div style="visibility: hidden; position: fixed;"
[style.left]="menuTopLeftPosition.x"
[style.top]="menuTopLeftPosition.y"
[matMenuTriggerFor]="rightMenu"></div>

<!-- standard material menu -->
<mat-menu #rightMenu="matMenu">
  <ng-template matMenuContent let-item="item">
    <button mat-menu-item>Clicked {% raw %}{{item.content}}{% endraw %}</button>
    <button mat-menu-item>Fixed value</button>
  </ng-template>
</mat-menu>
```
