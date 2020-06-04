---
title: 'Calculate the difference between two dates in Java'
description: 'Tutorial'
date: 2019-02-11T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'java'
color: '#7AAB13'
permalink: /calculate-dates
categories:
  - Java
tags:
  - Java
 
image: '/assets/img/'

introduction: 'Count the days between two dates'
---

## Avoid the pitfall of `between` and `until`

There are some use cases that require to count the number of days between two dates.
For example you need to count the days between the 1st of January 2019 and the 31th of December 2019.

`LocalDate` offers the method [`until`](https://docs.oracle.com/javase/8/docs/api/java/time/LocalDate.html) that is equivalent to
[`TemporalUnit.between(Temporal, Temporal)`](https://docs.oracle.com/javase/8/docs/api/java/time/temporal/TemporalUnit.html#between-java.time.temporal.Temporal-java.time.temporal.Temporal-)

The pitfall of these methods is that the first temporal object is inclusive and the second temporal object is exclusive.

<img src="{{site.baseurl}}/assets/img/uploads/2019/between.jpg" alt=""/>

In the first test you can see that between January 1st and December 31 there are 364 days because interval between the 2 dates doesn't include 365 full days.

```java
@Test
public static void daysBetween() {
  LocalDate firstDayOfTheYear = LocalDate.of(2019,1, 1);
  LocalDate lastDayOfTheYear = LocalDate.of(2019,12,31);

  // between Jan 01 2019 and Dec 31 2019 there are 364 days
  assertEquals(364, ChronoUnit.DAYS.between(firstDayOfTheYear, lastDayOfTheYear));
  // between Jan 01 2019 at 00:00 and Dec 31 2019 at 23.59999 there are 364 days
  assertEquals(364, ChronoUnit.DAYS.between(firstDayOfTheYear.atStartOfDay(), lastDayOfTheYear.atTime(LocalTime.MAX)));
  // between Jan 01 2019 at 15:00 and Dec 31 2019 at 14:59 there are 363 days
  assertEquals(363, ChronoUnit.DAYS.between(firstDayOfTheYear.atTime(15,00), lastDayOfTheYear.atTime(14, 59)));
}

```

In our second test we show that between January 1 midnight and December 31 at 23:59:59 we have 364 days.

In our third test we see that if the time of the begin date is later than the time of the end date, we could get 363 days as result.
363 is the total of _full_ days between the start and the end.

## How to count the days

Java doesn't offer the possibility to calculate the number of days using two inclusive dates.

If you want to count the number of days between two dates including them, you can use `between` or `until`
but you have to add 1 to the result or add 1 day to your end date:

```java
 assertEquals(365, ChronoUnit.DAYS.between(firstDayOfTheYear, lastDayOfTheYear) + 1);
```

```java
 assertEquals(365, DAYS.between(firstDayOfTheYear, lastDayOfTheYear.plus(1, DAYS)));
```


