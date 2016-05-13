# Calendar calculate

### Calculate the weekday of a day

To find out the day of the week for Julian or Gregorian calendar, we use Zeller formula

![Zeller Formula](http://i.imgur.com/IxM1Kza.png)

### Calculate the leap year

To see whether a year is a leap year or not, we follow this rule

Condition       | Leap year?
----------------|---------------
year % 4 != 0   | No
year % 4 == 0   | Yes
year % 100 == 0 | No
year % 400 == 0 | Yes

```ruby
def isLeap(year)
  return false if ((year % 4 != 0) || ((year % 100 == 0) && (year % 400 != 0)))
  return true
end
```

### Calculate the number of days in a month

```ruby
def daysIn(month, year)
  return (month == 2) ? (28 + isLeap(year)) : 31 - (month - 1) % 7 % 2
end
```

Source: http://huytd.github.io/posts/phuc-tap-hoa-datepicker.html
