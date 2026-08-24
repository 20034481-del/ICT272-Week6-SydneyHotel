# ICT272 Week 6 - Sydney Hotel

C# console program used for the Week 6 GitHub version control activity.

Student ID: 20034481

## About the program

A reservation program for a hotel. It asks for a customer name, the number of
nights (1-20) and whether room service is wanted, then works out the bill:

| Nights | Rate per night |
| ------ | -------------- |
| 1 - 3  | $100.00 |
| 4 - 10 | $80.50 |
| 11 - 20 | $75.30 |

Room service adds 10% to the total. At the end the program prints a summary
table of every reservation and reports the highest and lowest spending
customers.

## Running it

```
dotnet run
```

## Version history

**Initial commit** - the original program as provided in the lab.

**Fix room service case sensitivity and invalid number crash** - two changes:

1. Room service was compared with `roomService == "yes"`, so a customer who
   answered "Yes" or "YES" was never charged the 10% surcharge. Now compared
   as `roomService.Trim().ToLower() == "yes"`, which also tolerates stray
   spaces. A 3-night stay with room service now correctly bills $330 instead
   of $300.

2. The number of nights was read with `int.Parse`, which throws a
   `FormatException` and crashes the program if the user types anything that
   is not a whole number. Replaced with `int.TryParse` so bad input prints a
   message and asks again instead of terminating.
