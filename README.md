# age

A Flutter package to calculate someone's age in days, months, and years; in addition it can be used to find the difference between two dates.

> This is null safety version of https://pub.dev/packages/age <br>
> I'm not owner of this. © All rights reverse to `wixtime.com`

## Getting Started

In your flutter project add the dependency:

dependencies:
  ...
  age: ^0.0.1

For help getting started with Flutter, view the online documentation.

### Example

```dart
import 'package:age/age.dart';

void main() {
  DateTime birthday = DateTime(1990, 1, 20);
  DateTime today = DateTime.now(); //2020/1/24

  AgeDuration age;

  // Find out your age
  age = Age.dateDifference(
      fromDate: birthday, toDate: today, includeToDate: false);

  print('Your age is $age'); // Your age is Years: 30, Months: 0, Days: 4

  // Find out when your next birthday will be.
  DateTime tempDate = DateTime(today.year, birthday.month, birthday.day);
  DateTime nextBirthdayDate = tempDate.isBefore(today)
      ? Age.add(date: tempDate, duration: AgeDuration(years: 1))
      : tempDate;
  AgeDuration nextBirthdayDuration =
      Age.dateDifference(fromDate: today, toDate: nextBirthdayDate);

  print('You next birthday will be on $nextBirthdayDate or in $nextBirthdayDuration');
  // You next birthday will be on 2021-01-20 00:00:00.000 or in Years: 0, Months: 11, Days: 27
}
```
