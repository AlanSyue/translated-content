---
title: Date() constructor
slug: Web/JavaScript/Reference/Global_Objects/Date/Date
translation_of: Web/JavaScript/Reference/Global_Objects/Date/Date
---
{{JSRef}}

Creates a JavaScript **`Date`** instance that represents a single moment in time in a platform-independent format. `Date` objects contain a `Number` that represents milliseconds since 1 January 1970 UTC.

{{EmbedInteractiveExample("pages/js/date-constructor.html")}}

## Syntax

```plain
new Date()
new Date(value)
new Date(dateString)
new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]])
```

> **备注：** The only correct way to instantiate a new `Date` object is by using the {{jsxref("new")}} operator. If you simply call the `Date` object directly, such as `now = Date()`, the returned value is a string rather than a `Date` object.

### Parameters

There are four basic forms for the `Date()` constructor:

1. #### No parameters

    When no parameters are provided, the newly-created `Date` object represents the current date and time as of the time of instantiation.

2. #### Time value or timestamp number

    - `value`
      - : An integer value representing the number of milliseconds since January 1, 1970, 00:00:00 UTC (the ECMAScript epoch, equivalent to the UNIX epoch), with leap seconds ignored. Keep in mind that most [UNIX Timestamp](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html#tag_04_16) functions are only accurate to the nearest second.

3. #### Timestamp string

    - `dateString`

      - : A string value representing a date, specified in a format recognized by the {{jsxref("Date.parse()")}} method. (These formats are [IETF-compliant RFC 2822 timestamps](http://tools.ietf.org/html/rfc2822#page-14), and also strings in a [version of ISO8601](http://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.15).)

        > **备注：** Parsing of date strings with the `Date` constructor (and `Date.parse()`, which works the same way) is _strongly discouraged_ due to browser differences and inconsistencies.
        >
        > - Support for [RFC 2822](https://tools.ietf.org/html/rfc2822) format strings is by convention only.
        > - Support for ISO 8601 formats differs in that date-only strings (e.g. `"1970-01-01"`) are treated as UTC, not local.

4. #### Individual date and time component values

    Given at least a year and month, this form of `Date()` returns a `Date` object whose component values (year, month, day, hour, minute, second, and millisecond) all come from the following parameters. Any missing fields are given the lowest possible value (`1` for `day` and `0` for every other component).

    - `year`

      - : Integer value representing the year.

        Values from `0` to `99` map to the years `1900` to `1999`. All other values are the actual year. See the [example below](#Two_digit_years_map_to_1900_-_1999).

    - `monthIndex`
      - : Integer value representing the month, beginning with `0` for January to `11` for December.
    - `day` {{optional_inline}}
      - : Integer value representing the day of the month. The default is `1`.
    - `hours` {{optional_inline}}
      - : Integer value representing the hour of the day. The default is `0` (midnight).
    - `minutes` {{optional_inline}}
      - : Integer value representing the minute segment of a time. The default is `0` minutes past the hour.
    - `seconds` {{optional_inline}}
      - : Integer value representing the second segment of a time. The default is `0` seconds past the minute.
    - `milliseconds` {{optional_inline}}
      - : Integer value representing the millisecond segment of a time. The default is `0` milliseconds past the second.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
