
**Working with Date and time**

🥑 [Creation](#creation)

🥑 [Access date components](#access-date-components)

🥑 [Setting date components](#setting-date-components)

🥑 [Autocorrection](#Autocorrection)

🥑 [Date to number, date diff](#date-to-number-date-diff)

🥑 [Date.now()](#datenow)

🥑 [Benchmarking](#benchmarking)

🥑 [Date.parse from a string](#dateparse-from-a-string)

*****

### _Creation_

To instantiate a new Date object, we use syntax `new Date()` with one of the below options:

1. `new Date()`: Creates a Date object representing the current date and time.

   **For example:**

   ```javascript
   let now = new Date();
   alert(now); // displays the current date/time
   ```

2. `new Date(milliseconds)`: Creates a Date object with a time equivalent to the number of milliseconds passed since Jan 1st, 1970 UTC+0.

   **For example:**

   ```javascript
   let Jan01_1970 = new Date(0);
   alert(Jan01_1970); // displays 01.01.1970 UTC+0
   
   let Jan02_1970 = new Date(24 * 3600 * 1000);
   alert(Jan02_1970); // displays 02.01.1970 UTC+0
   ```

A timestamp is an integer representing the number of milliseconds that have elapsed since the beginning of 1970. Dates before Jan 1st, 1970 have negative timestamps.

For dates in string format, you can use `new Date(datestring)`. The string is parsed automatically using the same algorithm as `Date.parse()`.

**For example:**

```javascript
let date = new Date("2017-01-26");
alert(date);
```

For creating a date with specific components, use `new Date(year, month, date, hours, minutes, seconds, ms)`. The year must have 4 digits, but 2 digits are also accepted (interpreted as 19xx). Month starts from 0 (Jan) to 11 (Dec). If some parameters are missing, they default to 0.

**For example:**

```javascript
new Date(2011, 0, 1, 0, 0, 0, 0); // Jan 1, 2011, 00:00:00
new Date(2011, 0, 1); // Same as above, hours etc. default to 0
let date = new Date(2011, 0, 1, 2, 3, 4, 567); // Jan 1, 2011, 02:03:04.567
alert(date);
```

### _Access date components_

JavaScript provides methods to access various components of a Date object:

- `getFullYear()`: Gets the year (4 digits).
- `getMonth()`: Gets the month from 0 to 11.
- `getDate()`: Gets the day of the month (1 to 31).
- `getHours()`, `getMinutes()`, `getSeconds()`, `getMilliseconds()`: Accesses time components.

The `getYear()` method is deprecated due to its inconsistency in returning a 2-digit year. It's better to use `getFullYear()` instead.

For the day of the week, use `getDay()`, returning values from 0 (Sunday) to 6 (Saturday).

These methods return local time zone values. For UTC-based values, use `getUTCFullYear()`, `getUTCMonth()`, and `getUTCDay()`.

`getTime()` returns the timestamp (milliseconds since Jan 1, 1970 UTC+0), while `getTimezoneOffset()` retrieves the time zone difference in minutes between UTC and the local time zone.

**Use-case example:**

```javascript
// Create a new Date object
let date = new Date();

// Accessing various date components
console.log("Year:", date.getFullYear()); // Get the year (4 digits)
console.log("Month:", date.getMonth()); // Get the month (0 - 11)
console.log("Date:", date.getDate()); // Get the day of the month (1 - 31)
console.log("Hours:", date.getHours()); // Get the hour (0 - 23)
console.log("Minutes:", date.getMinutes()); // Get the minutes (0 - 59)
console.log("Seconds:", date.getSeconds()); // Get the seconds (0 - 59)
console.log("Milliseconds:", date.getMilliseconds()); // Get the milliseconds (0 - 999)

// Accessing day of the week
console.log("Day of the week:", date.getDay()); // Get the day of the week (0 - 6)

// Accessing UTC counterparts
console.log("UTC Year:", date.getUTCFullYear());
console.log("UTC Month:", date.getUTCMonth());
console.log("UTC Day:", date.getUTCDay());

// Other methods
console.log("Timestamp:", date.getTime()); // Get timestamp
console.log("Timezone Offset:", date.getTimezoneOffset()); // Get timezone offset
```

### _Setting date components_

The below methods enable the manipulation of various date and time components. Each method allows for the adjustment of specific aspects of a date object.

- `setFullYear(year, [month], [date])`
- `setMonth(month, [date])`
- `setDate(date)`
- `setHours(hour, [min], [sec], [ms])`
- `setMinutes(min, [sec], [ms])`
- `setSeconds(sec, [ms])`
- `setMilliseconds(ms)`
- `setTime(milliseconds)` (which sets the entire date based on milliseconds since January 1, 1970, UTC)

All methods except `setTime()` have a **UTC** variant, such as `setUTCHours()`.

Some methods can adjust multiple components simultaneously, like `setHours()`. If certain components are not specified, they remain unchanged.

**For example:**

```javascript
let today = new Date();

today.setHours(0);
alert(today); // today's date remains the same, but the hour is changed to 0

today.setHours(0, 0, 0, 0);
alert(today); // still today's date, now set precisely at 00:00:00
```

### _Autocorrection_

Autocorrection in Date objects seamlessly adjusts out-of-range values, such as transforming 32 Jan 2013 to 1st Feb 2013.

```javascript
let date = new Date(2013, 0, 32); // 32 Jan 2013 is corrected to 1st Feb 2013
alert(date); // Outputs: 1st Feb 2013
```

Date objects automatically adjust dates, like when adding 2 days to "28 Feb 2016" in a leap year.

**For example:**

```javascript
let date = new Date(2016, 1, 28); // 28th Feb 2016
date.setDate(date.getDate() + 2); // Add 2 days

alert(date); // Outputs: 1st Mar 2016
```

The below function is for finding dates after a set time, like 70 seconds from now.

```javascript
let date = new Date();
date.setSeconds(date.getSeconds() + 70); // Add 70 seconds

alert(date); // Outputs: the correct date
```

We can set zero or negative values, and the Date object handles it too.

**For example:**

```javascript
let date = new Date(2016, 0, 2); // 2nd Jan 2016

date.setDate(1); // Set day 1 of the month
alert(date); // Outputs: 1st Jan 2016

date.setDate(0); // Setting day 0 effectively sets it to the last day of the previous month
alert(date); // Outputs: 31st Dec 2015
```

### _Date to number, date diff_

Converting a Date object to a number gives a timestamp like `date.getTime()`. Easy to find the difference between dates in milliseconds.

**For example:**

```javascript
let start = new Date(); // Record the start time

// Perform a task
for (let i = 0; i < 100000; i++) {
  let doSomething = i * i * i;
}

let end = new Date(); // Record the end time

alert( `The task took ${end - start} milliseconds` );
```

The above code measures the time taken to execute a loop by calculating the difference between the end time `(end)` and the start time `(start)` in milliseconds.

### _Date.now()_

Instead of Date objects, we can use `Date.now()` for faster, memory-efficient timestamp retrieval. It's ideal for performance-focused tasks like JavaScript games, accurately measuring time without extra overhead.

**For example:**

```javascript
let start = Date.now(); // Capture the current timestamp

// Perform a task
for (let i = 0; i < 100000; i++) {
  let doSomething = i * i * i;
}

let end = Date.now(); // Task completed

alert( `The operation took ${end - start} ms` ); // Calculate and display the elapsed time
```

The above example

- Captures the current timestamp using `Date.now()` before the task begins.
- Once it completed, it records another timestamp using the same method to mark its end.
- By subtracting the start timestamp from the end timestamp, we calculate the duration of the operation in milliseconds.

### _Benchmarking_

Benchmarking date and time functions in JavaScript compares performance of methods calculating date differences. For example, comparing direct subtraction versus using `getTime()`.

In the below code, there are two functions defined. Both functions calculate the difference between two dates, but they use different methods to do so.

```javascript
function diffSubtract(date1, date2) {
  return date2 - date1;
}

function diffGetTime(date1, date2) {
  return date2.getTime() - date1.getTime();
}
```

Now we create a `bench` to benchmark these functions

```javascript
function bench(f) {
  let date1 = new Date(0);
  let date2 = new Date();

  let start = Date.now();
  for (let i = 0; i < 100000; i++) f(date1, date2);
  return Date.now() - start;
}
```

The above function measures the time taken to execute a given function `(f)` 100,000 times.

Initially, the benchmark runs without considering external interference. To counter this, it's run multiple times, alternating between functions for accuracy.

Refer to the below code;

```javascript
let time1 = 0;
let time2 = 0;

// Warm-up phase
bench(diffSubtract);
bench(diffGetTime);

// Benchmarking phase
for (let i = 0; i < 10; i++) {
  time1 += bench(diffSubtract);
  time2 += bench(diffGetTime);
}
```

Before benchmarking, functions are run once to optimize them. Then, each function is tested 10 times alternately to accumulate total execution time. Finally, results are displayed for accurate comparison.

### _Date.parse from a string_

The `Date.parse(str)` method is used to extract a date from a string. The string format must follow the pattern: **YYYY-MM-DDTHH:mm:ss.sssZ**

- YYYY-MM-DD represents the date: year-month-day.
- "T" serves as the delimiter.
- HH:mm:ss.sss denotes the time: hours, minutes, seconds, and milliseconds.
- The optional 'Z' segment indicates the time zone in the format +-hh:mm. A solitary 'Z' signifies UTC+0.
- Shorter variants such as YYYY-MM-DD or YYYY-MM or even YYYY are also acceptable.

When you invoke `Date.parse(str)`, it parses the string according to the specified format and returns the timestamp, which is the number of milliseconds from 1 Jan 1970 UTC+0. If the format is invalid, it returns NaN.

**For example:**

```javascript
let ms = Date.parse('2012-01-26T13:51:50.417-07:00');

alert(ms); // 1327611110417 (timestamp)
```

From the timestamp, you can instantiate a new Date object:

```javascript
let date = new Date( Date.parse('2012-01-26T13:51:50.417-07:00') );

alert(date);
```

The above code will output the date based on the provided timestamp.