 `[Unit]` - who, when, what must be ready first, conditions before running
 `[Service]` - how it runs, execution control
 `[Install]` - integration with targets
#### Dependecy
Requires=
Wants= (try to start other service)
BindsTo= (if others stops, stop me too)
#### Ordering
After=/Before=
#### Condition
Condition* = if false, then skip this unit
#### Assertion
Assertion* = if false, then fail this unit  

Links:

202511061717

