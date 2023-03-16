# Shaking motion NEEM data
This directory contains raw NEEM data files for shaking motion used for sprinkling salt on top of breakfast dish.

## Link to visualize NEEM on openEASE
https://data.open-ease.org/QA?neem_id=641064a2ba2ba183b56ca0de

## Queries to visualize NEEM on openEASE
1. Get the maximum event that happened during the experiment.

```prolog
findall([Duration, Evt],
  (  event_interval(Evt, Begin, End),
     number(End),
     Duration is End - Begin
  ),
  Durations),
max_member([MaxDuration, LongestEvt], Durations)
```


