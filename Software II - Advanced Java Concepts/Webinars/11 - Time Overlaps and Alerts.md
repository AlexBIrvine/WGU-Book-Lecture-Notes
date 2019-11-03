---
Date: 2019/11/02
Length: 49:56
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [Time Overlaps and Alerts](https://wgu.adobeconnect.com/pyt1ke5o2bys/)

<u>**Summary**</u>:

Plan:

- Checking for overlapping times using LocalDateTime methods
- Work with the `ChronoUnit` ENUM

---

## LocalDateTime Methods for Time Overlaps (00:47 - 01:40)

LocalDateTime class provides `isAfter()` & `isBefore()` methods to check if a Time is between two Times.  
LocalDateTime class provides `equals()` method for checking if times are the same.

---

## Programming Exercise (1:40 - 17:10) Checking for Time Overlaps

```java
LocalDateTime start = LocalDateTime.of(2019, 11, 02, 23, 51);       // 2019/11/2 at 11:51 PM ET
LocalDateTime end = LocalDateTime.of(2019, 11, 03, 00, 00);         // Midnight 2019/11/3
LocalDateTime check = LocalDateTime.of(2019,11,02,23,55);           // Falls between the two times
LocalDateTime badCheck = LocalDateTime.of(2019,11,02,10,55);        // Doesn't fall between the two times

//Checks all possible combinations
if (check.isAfter(start) && check.isBefore(end))
    System.out.println("LocalDateTime check is in between!");
else if (check.isAfter(start) && !check.isBefore(end))
    System.out.println("LocalDateTime check is after the two times");
else if (!check.isAfter(start) && check.isBefore(end))
    System.out.println("LocalDateTime check is before the two times");
else if (check.equals(start))
    System.out.println("LocalDateTime check is equal to the start time");
else if (check.equals(end))
    System.out.println("LocalDateTime check is equal to the end time");
else
    System.out.println("<<< Danger Dragon >>>>   If you are seeing this, something is terribly wrong");
```

---

## ChronUnit and ENUMS (17:28 - 20:10)

Useful for running an alert when the time falls between within a specific range (for the 15-minute alert)

### What is an Enum? (18:00 - 19:20)

A class that provides a finite collection of CONSTANTS.  
Think of this as an array of CONSTANTS.  
ENUM can have Constructors, Fields ,and Methods.

### What is a ChronoUnit? (19:20 - 20:10)

An ENUM that provides members for performing calculations on TemporalValues (LocalDate & LocalTime).  
The two useful CONSTANTS for us is `HOURS` and `MINUTES`.

---

## Programming Exercise (20:15 - END) Differentiating Temporal Values

```java
LocalTime startTime = LocalTime.of(00, 30);                                 //12:30 AM
LocalTime currentTime = LocalTime.of(now());                                //My current time of 12:14 AM
long timeDifference = ChronoUnit.MINUTES.between(currentTime, startTime);   //Stores the difference in minutes between two times

System.out.println(timeDifference);                                         // OUTPUT:   16

//Check to see if time is within 15 minute range
if (timeDifference > 0 && timeDifference <= 15)
    System.out.println("ALERT:  Within 15 minutes");
```

<u>NOTE:</u>  
The speaker goes into further coding examples around 35:30 by adding `else if` statements if the appointment is over, etc.,  
Not taking notes on this part since this is trivial stuff at this point in the degree, and I'm lazy.  
He also added a hack where he adds 1 to the timeDifference, since that number is rounded to the nearest minute and his output was off by 1.  
I'm okay with being a minute off for cleaner code.  
If you need something more precise, use `seconds`.
