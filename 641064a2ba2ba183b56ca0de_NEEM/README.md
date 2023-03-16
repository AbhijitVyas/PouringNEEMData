# Shaking motion NEEM data
This directory contains raw NEEM data files for shaking motion used for sprinkling salt on top of breakfast dish.

## Queries to visualize NEEM on openEASE
1. findall([Duration, Evt],
  (  event_interval(Evt, Begin, End),
     number(End),
     Duration is End - Begin
  ),
  Durations),
max_member([MaxDuration, LongestEvt], Durations)



