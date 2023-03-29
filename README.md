# Pouring VR experiment data
Repository contains all raw NEEM data files that were recorded from VR environment.

## Watch how to query NEEMs on openEASE platform
https://user-images.githubusercontent.com/17174958/225921309-f2780105-dfd6-40e4-97f8-ceb4a8385fe4.mp4

## Queries to visualize NEEM on openEASE
1. What is the longest event that occurred?

```prolog
findall([Duration, Evt],
  (  event_interval(Evt, Begin, End),
     number(End),
     Duration is End - Begin
  ),
  Durations),
max_member([MaxDuration, LongestEvt], Durations).
```

2. What was source container while pouring?
```prolog
has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
executes_task(Act, Tsk), has_participant(Act, Obj), 
has_type(Role, soma:'SourceContainer'), triple(Obj, dul:'hasRole', Role).
```

3. What was destination container while pouring?
```prolog
has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
executes_task(Act, Tsk), has_participant(Act, Obj), 
has_type(Role, soma:'DestinationContainer'), 
triple(Obj, dul:'hasRole', Role).
```

4. How long pouring lasted?
```prolog
has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
executes_task(Act, Tsk), event_interval(Act, Begin, End).
```

5. Which hands participated during pouring?
```prolog
has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
executes_task(Act, Tsk), has_type(Hand, soma:'Hand'), 
has_participant(Act,Hand).
```


6. What motion was used for pouring?
```prolog
has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
executes_task(Act, Tsk), 
triple(Motion, 'http://www.ontologydesignpatterns.org/ont/dul/DUL.owl#classifies', Act).
```


7. What was maximum angle while pouring?
```prolog
has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
executes_task(Act, Tsk), has_participant(Act, Obj), 
has_type(Role, soma:'SourceContainer'), 
triple(Obj, dul:'hasRole', Role), 
triple(Obj, dul:'hasRegion', Region), 
triple(Region, 'http://www.ease-crc.org/ont/SOMA-OBJ.owl#hasJointPositionMax', AngleMax).
```

8. What was minimum angle while pouring?
```prolog
has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
executes_task(Act, Tsk), has_participant(Act, Obj), 
has_type(Role, soma:'SourceContainer'), 
triple(Obj, dul:'hasRole', Role), 
triple(Obj, dul:'hasRegion', Region), 
triple(Region, 'http://www.ease-crc.org/ont/SOMA-OBJ.owl#hasJointPositionMin', AngleMin).
```
9. Find pouring substance with its role and the quantity.

```prolog
findall([Obj, Role],
  (  has_type(Tsk, 'http://www.ease-crc.org/ont/SOMA-ACT.owl#Pouring'),
	executes_task(Act, Tsk), has_participant(Act, Obj), 
	has_type(Obj, dul:'Substance'), triple(Obj, dul:'hasRole', Role)
  ),
Objects), length(Objects, Quantity)
```
