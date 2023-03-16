# PouringNEEMData
This repo contains all raw NEEM data files that were recorded from RobCog VR environment.

## Queries to visualize NEEM on openEASE
1. What is the longest event that occurred?

```prolog
findall([Duration, Evt],
  (  event_interval(Evt, Begin, End),
     number(End),
     Duration is End - Begin
  ),
  Durations),
max_member([MaxDuration, LongestEvt], Durations)
```

2. What was source container while pouring?

3. What was destination container while pouring?

4. How long pouring lasted?

5. What objects participated during pouring?

6. 
