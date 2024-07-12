
--- 
tags: [[JS Date]]
date: 2024-07-11

---
### Time-related Constants
These constants are referenced by algorithms in the following sections.

HoursPerDay = 24
MinutesPerHour = 60
SecondsPerMinute = 60
msPerSecond = 1000𝔽
msPerMinute = 60000𝔽 = msPerSecond × 𝔽(SecondsPerMinute)
msPerHour = 3600000𝔽 = msPerMinute × 𝔽(MinutesPerHour)
msPerDay = 86400000𝔽 = msPerHour × 𝔽(HoursPerDay)

### Time-related Constants
These constants are referenced by algorithms in the following sections.

HoursPerDay = 24
MinutesPerHour = 60
SecondsPerMinute = 60
msPerSecond = 1000𝔽
msPerMinute = 60000𝔽 = msPerSecond × 𝔽(SecondsPerMinute)
msPerHour = 3600000𝔽 = msPerMinute × 𝔽(MinutesPerHour)
msPerDay = 86400000𝔽 = msPerHour × 𝔽(HoursPerDay)

### MonthFromTime ( t )

The abstract operation MonthFromTime takes argument t (a [finite](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#finite) [time value](https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-time-values-and-time-range)) and returns an [integral Number](https://tc39.es/ecma262/multipage/notational-conventions.html#integral-number) in the [inclusive interval](https://tc39.es/ecma262/multipage/notational-conventions.html#inclusive-interval) from +0𝔽 to 11𝔽. It returns a Number identifying the month in which t falls. Note that MonthFromTime(+0𝔽) = +0𝔽, corresponding to Thursday, 1 January 1970. It performs the following steps when called:

1. Let inLeapYear be [InLeapYear](https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-inleapyear)(t).
2. Let dayWithinYear be [DayWithinYear](https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-daywithinyear)(t).
3. If dayWithinYear < 31𝔽, return +0𝔽.
4. If dayWithinYear < 59𝔽 + inLeapYear, return 1𝔽.
5. If dayWithinYear < 90𝔽 + inLeapYear, return 2𝔽.
6. If dayWithinYear < 120𝔽 + inLeapYear, return 3𝔽.
7. If dayWithinYear < 151𝔽 + inLeapYear, return 4𝔽.
8. If dayWithinYear < 181𝔽 + inLeapYear, return 5𝔽.
9. If dayWithinYear < 212𝔽 + inLeapYear, return 6𝔽.
10. If dayWithinYear < 243𝔽 + inLeapYear, return 7𝔽.
11. If dayWithinYear < 273𝔽 + inLeapYear, return 8𝔽.
12. If dayWithinYear < 304𝔽 + inLeapYear, return 9𝔽.
13. If dayWithinYear < 334𝔽 + inLeapYear, return 10𝔽.
14. [Assert](https://tc39.es/ecma262/multipage/notational-conventions.html#assert): dayWithinYear < 365𝔽 + inLeapYear.
15. Return 11𝔽.


### References:
https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-time-values-and-time-range
---



