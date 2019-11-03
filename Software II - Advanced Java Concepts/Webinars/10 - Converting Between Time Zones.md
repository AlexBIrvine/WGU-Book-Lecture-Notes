---
Date: 2019/11/02
Length: 41:14
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [Converting Between Time Zones](https://wgu.adobeconnect.com/p6uz30g79pvw/)

<u>**Summary**</u>:

Plan:

- Understand ZonedDateTime and ZoneId Classes
- List and Filter TimeZones
- Convert between Time Zones

---

## ZonedDateTime (00:32 - 02:23)

Object that consists of date, time and time zone.

**It has 4 parts:**

1. Date
2. Time
3. Offset (Time difference between local and UTC)
4. Time Zone

---

## ZonedDateTime Static Methods (02:25 - 04:35)

<u>**now()**</u>: Displays current date, time & zone of system.  
<u>**of()**</u>: Used to explicitly create a ZonedDateTime object.  
<u>**toInstant()**</u>: Converts ZonedDateTime to UTC.  
<u>**withZoneSameInstant()**</u>: Converts ZonedDateTime to another zone.  
<u>**atZone()**</u>: Converts UTC to a ZonedDateTime using zone ID.

---

## ZoneId (04:37 - 06:00)

Consists of Continent or Country, a /, then location (state, province, etc.,)  
<u>**of()**</u>: static method for creating a ZoneId.

Examples:

- Europe/Guernsey
- America/Grand_Turk
- US/Pacific-New
- US/Alaska

---

## Programming Exercise (06:00 - 13:30) Listing Time Zones in your OS

```java
public static void getAllZones() {
    ZoneId.getAvailableZoneIds().stream().forEach(System.out::println);
}

public static void getAllZonesByContinent(String continent) {
    ZoneId.getAvailableZoneIds().stream().filter(c -> c.contains(continent)).forEach(System.out::println);
}
```

---

### Aside... (double colon)

The double colon operator used above is known as the <u>**method reference operator**</u>. It's used to shorted lambda expressions.

Syntax: `<Class name>::<method name>`

The two lines of following code are equivalent:

```java
stream.forEach(s -> System.out.println(s));
stream.forEach(System.out::println(s));
```

---

## Programming Exercise (13:40 - 35:15) Converting Between Time Zones

```java
//Setup Paris Time
LocalDate parisDate = LocalDate.of(2019, 11, 2);    //Today's date                  This can be the values from a DatePicker GUI
LocalTime parisTime = LocalTime.of(21, 59);         //Now time (currently 9:59 PM)  This can be the values from a ComboBox   GUI
ZoneId parisZoneId = ZoneId.of("Europe/Paris");
ZonedDateTime parisZDT = ZonedDateTime.of(parisDate, parisTime, parisZoneId);

//Setup Local Timezone Id(based on system)
ZoneId localZoneId = ZoneId.of(TimeZone.getDefault().getID());

//Paris time to UTC/GMT
Instant parisToGMT = parisZDT.toInstant();

//Paris time to local time
ZonedDateTime parisToLocalZDT = parisZDT.withZoneSameInstant(localZoneId);

//UTC/GMT to local time
ZonedDateTime utcToLocalZDT = parisToGMT.atZone(localZoneId);

//Printing out values
System.out.println("Paris: " + parisZDT);
System.out.println("Paris to GMT: " + parisToGMTInstant);
System.out.println("GMT to local: " + utcToLocalZDT);
System.out.println("GMT to LocalDate: " + utcToLocalZDT.toLocalDate());
System.out.println("GMT to localTime: " + utcToLocalZDT.toLocalTime());
```

---

## Programming Exercise (35:20 - END) Inserting new time classes into SQL

(uses the code above)

```java
String date = String.valueOf(utcToLocalZDT.toLocalDate());
String time = String.valueOf(utcToLocalZDT.toLocalTime());
String dateTime = date + " " + time;                        //You can insert this string into the database.
System.out.println(dateTime);
```
