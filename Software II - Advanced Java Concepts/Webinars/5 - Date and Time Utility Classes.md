---
Date: 2019/10/01
Length: 1:15:08
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [Date and Time Utility Classes](https://wgu.adobeconnect.com/plqiqvw32s3h/)

<u>**Summary**</u>:

Plan:

- Construct Dates and Times
- Work with Time Zones
- Retrieve Geographic information

---

## The Calendar Class (01:00 - 12:26)

Abstract singleton class that used to get date information. You must use the `getInstance()` method to initiate.

```java
//Create calendar object
Calendar myCalendar = Calendar.getInstance();

//Display Date & Time
System.out.println(myCalendar.getTime());                       //Prints "Thu Oct 03 18:12:34 EDT 2019"

//get() will retrieve info based on parameter.  Returns INT.
//Use Calendar constants
System.out.println(myCalendar.get(Calendar.HOUR_OF_DAY));       //Prints "18"
System.out.println(myCalendar.get(Calendar.YEAR));              //Prints "2019"

//Change Date and TIme info with set() method
//1st parameter is WHAT to change, 2nd is value to change to
myCalendar.set(Calendar.YEAR, 2077);
System.out.println(myCalendar.get(Calendar.YEAR));              //Prints "2077"

//Alternatively, set can be passed  6 parameters to hard set the info
//Year, month, day, hour, minute, second
myCalendar.set(2020, 3, 16, 00, 00, 00);                        //Sets to 2020/04/16 at midnight.

```

---

## The GregorianCalendar Class (12:26 - 17:58)

Subclass of Calendar, includes more methods (like isLeapYear()).  
Since it's a subclass, all methods in the Calendar object are available in the GregorianCalendar object.

```java
//Create GregorianCalendar Object
GregorianCalendar myCalender = new GregorianCalendar();

// new method, checks if  year is leap year
System.out.println(myCalendar.isLeapYear(2077));
```

---

## The TimeZone Class (17:59 - 1:001:00)

GMT is the center of all time zones (at zero). Think UK.

_The speaker goes into great detail on how timezones work.  
I'm a project coordinator, this is 2nd nature. **NO NOTES!**_

.getAvailableIDs() can take a parameter of the offset integer (-180000000 for ET)  
and display only results of that offset.

```java
//Get computer's  default time zone
TimeZone myTime = TimeZone.getDefault();
System.out.println(myTimeZone);                     //prints a large amount of info
System.out.println(myTimeZone.getID());             //prints "America/New_York"
System.out.println(myTimeZone.getDisplayName());    //prints "Eastern Time Zone"

//Display all time zones
for(String ID: TimeZone.getAvailableIDs()) {
    System.out.println(ID);                         //prints all Time Zone IDs
}

//Change Time Zone and display time
TimeZone.setDefault(TimeZone.getTimeZone("JST"));   //Changes default time zone to Japan's.

//Adjust time zone  [Displays  time based on UK time]
//  {I'm shocked the teacher didn't put this in a method}

//Create Scanner and get hour from user
Scanner keyboard =  new Scanner(System.in);
System.out.print("Enter meeting time in UK time: ");
int hour = keyboard.nextInt();

//Sets time zone to UK default
TimeZone.setDefault(TimeZone.getTimeZone("GB"));

//Create calendar and change hour of day, print UK time
Calendar myCalendar = Calendar.getInstance();
myCalendar.set(Calendar.HOUR_OF_DAY, hour);
System.out.println("UK: " + myCalendar.getTime());

//Sets time zone back to default, print my time
TimeZone.setDefault(myTimeZone);
System.out.println("Local Time: " + myCalendar.getTime());
```

Around 58:10 he goes into brief detail about SimpleTimeZone Class.  
SimpleTimeZone is a concrete class, and if it has any other benefit teacher doesn't say.

---

## The Locale Class (1:01:38 - END)

Locale is a specific Geographical region.  
Gets country names, codes, formatting and other region specific things.

```java
//Create Locale Object & Display info
Locale myLocale = Locale.getDefault();
System.out.println(myLocale);                       //Prints "en_US"
System.out.println(myLocale.getCountry());          //Prints "US"
System.out.println(myLocale.getDisplayCountry());   //Prints "United States"
System.out.println(myLocale.getDisplayLanguage());  //Prints "English"
System.out.println(myLocale.getLanguage());         //Prints "en"
System.out.println(myLocale.getISO3Country());      //Prints "USA"

//Display all Locales
for (Locale locale : Locale.getAvailableLocales()) {
    System.out.println(locale);
}

//Create Locale with constructor
Locale jpLocale = new Locale("ja", "JP");
System.out.println(jpLocale.getDisplayName());      //Prints "Japanese (Japan)"

//Create Locale with Locale fields
Locale canadaLocale = Locale.CANADA;
System.out.println(canadaLocale.getDisplayName());      //Prints "English (Canada)"
```
