---
id: 885
title: 'Angular and D3.js &#8211; tutorial'
date: 2017-02-10T00:25:39+00:00
author: Marco Molteni
layout: post
main-class: 'angular'
guid: https://marco.dev/?p=885
permalink: /2017/02/10/angular-and-d3-js-tutorial/
image: /wp-content/uploads/2017/03/logo-d3-100x12.png
categories:
  - Angular
  - Angular 2
  - d3.js
  - Demo Application
  - tutorial
tags:
  - Angular
  - Angular 2
  - d3.js
---
Goal: use the [D3.js](https://d3js.org) library in an Angular project.

<img class="alignnone size-full wp-image-884" src="{{site.baseurl}}/assets/img/uploads/2017/02/Ohne-Titel.png?resize=842%2C484" data-recalc-dims="1" />

Here the steps to integrate the library with Angular.

In the `package.json` we have to declare the dependencies with d3:

``` javascript
    "@types/d3": "^4.4.1",
    "@types/d3-scale": "^1.0.6",
    "d3": "^4.5.0",
    "d3-scale": "^1.0.4",
```    

In `vendor.ts`:
``` javascript
    // d3.js
    import 'd3/build/d3.min';
    import 'd3-scale/build/d3-scale.min';
```

In the [component](https://github.com/marco76/SpringAngular2TypeScript/blob/master/webClient/src/app/components/d3.component.ts) that will generate the view you have to import the d3 types:

``` javascript
    import * as d3 from "d3";
    import * as d3scale from "d3-scale";
```    

In the component we declare the style used and we reference the external xml

``` typescript
    @Component({
        selector: 'd3-example',
        templateUrl:'../html/d3.html',
        providers: [ConstantsService, Location],
        styles:[`.chart div {
        font: 10px sans-serif;
        background-color: steelblue;
        text-align: right;
        padding: 3px;
        margin: 1px;
        color: white;
        }`],
        encapsulation: ViewEncapsulation
            .None
        })
```    

The external html simply declare the object that will be modified by the library (chart):

``` typescript
    <h3>Example with D3</h3>
    <div class="chart"></div>
```    

Your class has to implement [AfterViewInit](https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html). This method is called after that Angular initialises the component's view and child views.

`export class D3Component implements OnInit, AfterViewInit`

``` typescript
    ngAfterViewInit() {
        var data = [10, 20 ,30 ,15, 4, 26, 33];
        d3.select(".chart")
            .selectAll("div")
            .data(data)
            .enter().append("div")
            .style("width", function(d) { return d*10 + "px"; })
            .text(function(d) { return d; });
    }
```