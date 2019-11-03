---
Date: 2019/10/09
Length: 42:43
---

Video: [Project Getting Started](https://protect-us.mimecast.com/s/yevcCL91x8cgg60rf1oyyS?domain=wgu.adobeconnect.com)

<u>**Summary**</u>:

---

[The intro is a joining in the middle of a conversation.]

## Intro? (00:00 - 11:36)

What's gone over / questions answered:

- How to get the connection string for database.
- A: We will need to put in data in the database.
- A: Use `auto increment` for primary keys.
- How to add MYSQL driver.

---

## Requirement A (11:38 - 14:20)

- **NO GUI REQUIRED!** You can create a CLI program.
- Only 2 languages required, one english. Google translate is okay.
- Use resource bundles (see localization chapter)
- Change label of the login screen based on locale.
- **ONLY THE LOGIN SCREEN HAS LANGUAGE REQUIREMENTS**.
- **Don't use dropdown to chose local. MUST BE BASED ON COMPUTER(JVM) TIME/ZONE**

---

## Requirement B (14:21 - 15:25)

- "Maintain" means editing & deleting.

---

## Requirement C (15:28 - 16:00)

- Just use lambda expressions anywhere.
- Can be done last since non-lambda methods will be replaced.

---

## Requirement D (16:01 - 19:20)

- Calendar doesn't have to be graphic! Can be a TableView that lists appointments.
- Often people use a radio button for the view (week/month)
- **DON'T USE CALENDAR FX**
- You _can_ build your own with a grid pane container. Not needed.

---

## Requirement E (19:21 - 20:40)

- Evaluator will change the time zone on their system to test changes.
- **Store everything in UTC in database**.

---

## Requirement F (20:41 - 23:10)

- Try/catch block, throws clause, assertions...
- **Business hours is checked on entry only.**
- Use ComboBox for hours/minutes & restrict them to only schedule in business hours.

---

## Requirement G (23:11 - 23:30)

- Look up online examples (old way vs new way).

---

## Requirement H (23:31 - 24:10)

- Only required on login.
- Alert should provide details (what it is, and who it's with).

---

## Requirement I (24:11 - 24:32)

- Reports can be TableView / ListView

---

## Requirement J (24:33 - 24:55)

- **Logger class should be used.**

---

## ERD Explanation (25:15 - 30:00)

- Not all tables/fields will be used.
- Reminder Table won't be used
- IncrementTypes Table won't be used
- Use "CreatedBy" field in Appointment data to link user.

---

## Other:

- Email professor about code example for database updating? (about 32:30) **(C195DatabaseExample)**
- See FAQ for more info.
- Don't do anything extra, it makes the evaluator's job harder. Make their life easy.
