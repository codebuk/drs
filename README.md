# drs
Notes on the serial communication protocol to the transport
State INIT

Aim:  The transporter should be at the postion "over the flip and drop compartment"
glass lid closed

INIT---01- (Positioning drive)
If the transporter is not at the position "over the flip and drop compartment", there will be done a positioning drive till to the position "over the magazine". The positioning drive remains undone, if the the transporter is at the position "over the magazine". Otherwise:

Transporter slowly to the left till to the position "over the magazine". If the position of it was already on the left side of it, this will be detected over a timeout. The transporter will be driven for 0,8s slowly to the right to drive it free. If a second try fails also to drive the transporter slowly to the position "over the magazine", the second timeout will be screened as an error on your monitor. Another possible error: Housing is open.

INIT---01-TO: On the drive "slowly left", the contactor "over the magazine" has not been activated.
INIT---01-HO: The housing has been opened.

INIT---02- (Drive to the "neutral" position)

Transporter "slowly right" till to the position "over the flip and drop compartment". Failure is going to be detected by a timeout. Another possible error: Housing is open.

INIT---02-TO: On the drive "slowly right", the contactor "over the flip and drop compartment" has not been activated.
INIT---02-HO: The housing has been opened.

Action INIT---03- (Closing of the glass lid)
Appears, if not happened yet. Error: Timeout, glass lid is not closed and housing is open.

INIT---03-TO: During the closing of the glass lid, the contactor "glass lid not open" has not been activated.
INIT---03-JM: During the closing of the glass lid, the contactor "glass lid closed" has not been activated (Jam).
INIT---02-HO: The housing has been opened.

State LOAD

Aim (magazine is full):
There is a fiche on the LED-panel
The glass lid is closed
Transporter is in position "before the flip and drop compartment"

Aim (magazine is empty):
The LED-panel is empty
The glass lid is open

Transporter is in position "over the flip and drop compartment"

LOAD---01- (Opening of the glass lid)

Appears, if not happened in the UNLOAD state. Error: Timeout and housing is open.

LOAD---01-TO: During the opening of the glass lid, the contactor "glass lid open" has not been activated.
LOAD---01-HO: The housing has been opened.

Action LOAD---02- (The Drive "fast left" till "before the magazine")

The transporter will be racked in for 0,2s "slowly left" and then accelerated to "fast left". By reaching the position "before the magazine", the drive will be cut off for 0,2s. Error: Timeout and housing is open.

LOAD---02-TO: During the "fast drive left", the contactor "before the magazine" has not been activated.
LOAD---02-HO: The housing has been opened.

LOAD---03- (The drive "slowly left" till "over the the magazine")

The transporter will be driven "slowly left" till to the position "over the magazine". Error: Timeout and housing open.

LOAD---03-TO: During the "slow drive left", the contactor "over the magazine" has not been activated.
LOAD---03-HO: The housing has been opened.

LOAD---04- (The drive to the "waiting" position when the magazine is empty)

The transporter tries to ingest a fiche till its pressure sensor activates or a fixed latency has been transcended. If the latency has been transcended, the transporterfan is going to be shut down and the transporter is going to be driven "slowly right" till to the position "over the flip and drop compartment". Error: Timeout and housing is open. Otherwise: The magazine is empty.

LOAD---04-TO: During the slow drive right, the contactor "over the flip and drop compartment" has not been activated.
LOAD---04-HO: The housing has been opened.
LOAD---04-EE: The magazine is empty.??????????

Action LOAD---05- (Fiche-Seperation)

The pressure sensor has been activated. We assume now that the transporter ingested minimum one fiche. To peel the fiche from possible stucked fiches, the seperator-fan will be activated after 50ms for 6s. 0,25s after shutdown of the seperator-fan, the transporter will be driven for 90ms "slowly left" to avoid edges in the fiche-material during ingesting it. Error: none.

Action LOAD---06- (The drive "slowly right" till "before the magazine")

The transporter drives with ingested fiche "slowly right" till to the position "before the magazine". Error: Timeout and housing open. The Timeout-Error will be interpreted as 
a precaution as a stucked fiche.

LOAD---06-JM: During the "slow drive" right, the contactor "before the magazine" has not been activated. This will be interpreted as a precaution as a stucked fiche (jam).
LOAD---06-HO: The housing has been opened.

LOAD---07- (The drive "fast right" till "before the LED-panel")

The transporter drives with ingested fiche "fast right" till to the position "before the LED- panel". Error: Timeout and housing open.

LOAD---07-TO: During the "fast drive right", the contactor "before the LED-panel" has not been activated.

LOAD---07-HO: The housing has been opened.

2.8 Action LOAD---08- (The drive "slowly right" till "over the LED-panel")

The transporter drives with ingested fiche "slowly right" till to the position "over the LED- panel". Error: Timeout and housing open.

LOAD---08-TO: During the "slow drive right", the contactor "over the LED-panel" has not been activated.
LOAD---08-HO: The housing has been opened.

LOAD---09- (Fiche-Dropping)

The transporterfan will be shut down. After 1s there will be a forced dropping. For that purpose the transporterfan will be run in reverse direction for 0,2s. After that, there will be a latency of 0,3s. Error: none.

LOAD---10- (The drive to the "waiting" position)

The transporter will be driven for 0,2s "slowly left" and then accelerated to "fast left". After reaching the position "before the flip and drop compartment", the motor will be shut down for 0,2s. Error: Timeout and housing is open.

LOAD---10-TO: During the "fast drive left", the contactor "before the flip and drop compartment" has not been activated.
LOAD---10-HO: The housing has been opened.


 LOAD---11- (Close glass lid)

Error: Timeout, glass lid is not closed and housing is open.

LOAD---11-TO: During the closing of the glass lid, the contactor "glass lid not open" has not been activated.
LOAD---11-JM: During the closing of the glass lid, the contactor "glass lid closed" has not been activated (Jam).
LOAD---11-HO: The housing has been opened.

3 State UNLOAD

Aim:
The last fiche is dropped down
The glass lid is open
The transporter is in the position "over the flip and drop compartment"

Action UNLOAD-01- (Opening of the glass lid and the suction)

Error: Timeout and housing is open.
UNLOAD-01-TO: During the opening of the glass lid, the contactor "glass lid open" has not been activated.
UNLOAD-01-HO: The housing has been opened.

Action UNLOAD-02- (The drive "fast right" till "before the LED-panel")

The transporter will be driven for 0,2s "slowly right" and then accelerated to "fast right". After reaching the position "before the LED-panel", the motor will be shut down for 0,2s. Error: Timeout and housing open.

UNLOAD-02-TO: During the "fast drive right", the contactor "before the LED-panel" has not been activated.

UNLOAD-02-HO: The housing has been opened.

Action UNLOAD-03- (The drive "slowly right" till "over the LED-panel")

The transporter drives "slowly right" till to the position "over the LED-panel". Error: Timeout and housing is open. The Timeout-error will be interpreted as a precaution as a stucked fiche.

UNLOAD-02-JM: During the "slow drive right", the contactor "over the LED-panel" has not been activated. This will be interpreted as a precaution as a stucked fiche (jam).

UNLOAD-02-HO: The housing has been opened.

Action UNLOAD-04- (To the "waiting" position when the LED-panel is empty)

The transporter tries to ingest a fiche till its pressure sensor activates or a fixed latency has been transcended. If the latency has been transcended, the transporterfan is going to be shut down and the transporter is going to be driven "slowly left" till to the position "before the flip and drop compartment.". Error: Timeout and housing is open.

UNLOAD-04-TO: During the "slow drive left", the contactor "before the flip and drop compartment" has not been activated.

UNLOAD-04-HO: The housing has been opened.

Action UNLOAD-05- (The drive "slowly left" till "before the LED-panel")

The pressure sensor has been activated. The transporter drives with ingested fiche "slowly left" till to the position "before the LED-panel". Error: Timeout and housing is open. The Timeout-error will be interpreted as a precaution as a stucked fiche.

UNLOAD-05-JM: During the "slow drive left", the contactor "before the LED-panel" has not been activated. This will be interpreted as a precaution as a stucked fiche (jam).
UNLOAD-05-HO: The housing has been opened.

UNLOAD-06- (The drive "fast left" till "before the flip and drop compartment")

The transporter drives with ingested fiche "fast left" till to the position "before the flip and drop compartment" Fehler: Timeout and housing open.

UNLOAD-06-TO: During the "fast drive left", the contactor "before the flip and drop compartment" has not been activated.
UNLOAD-06-HO: The housing has been opened.

UNLOAD-07- (The drive "slowly left" till "over the flip and drop compartment")

The transporter drives with ingested fiche "slowly left" till to the position "over the flip and drop compartment." Error: Timeout and housing is open.

UNLOAD-07-TO: During the "slow drive left", the contactor "over the flip and drop compartment" has not been activated.
