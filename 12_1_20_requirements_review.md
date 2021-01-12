# Alarm Requirements Review

Attendees: Greg White, Ernest Williams, Mike Zelazny, Chris Zimmer, William Colocho, Peter Schuh, Jackie Garrahan
Date: 12/1/20

The purpose of this meeting is to serve as a final stakeholder review before proceeding with requirement document formalization.

## Agenda
1. Discuss document structure, priority buckets, and use case/feature supplements
2. Review requirements
    * Solicit justification in case of disagreement
    * Address all requirements flagged for conflicting or absent priority rankings

## Minutes
MZ: What is exact definition of passive and active states?  
EW: Exactly from definition in Alarm Handler   
MZ: As written in requirement, suggests local behavior instead of passive behavior  
WC: Couldn't we accomplish local behavior on dev? No one should be developing on prod  
GW: Process/architecture modification should be included in the document  
EW: Inside alarm room, may want to trouble shoot locally  
JG: Survey suggests low local mode utilization  
MZ: People will expect to have a local mode   

RESOLUTION: Put passive and active definitions into definitions sections. Additionally, add local mode requirement. Correct passive and active mode requirement.

JG: Want to confirm that the wording of requirement 3.4.1.1 has satisfied Greg's concerns mentioned during EED presentation on 11/5/2020   
GW: Updated requirement has clarified requirement  

GW: Does Feature F10 (Analytics plugin framework) imply archiving of alarms?  
MZ: How big is the log file?  
JZ: Everything currently written for 60 days   
GW: F10 low priority  
JZ: Agree  
CONSENSUS: F10 is development priority 2

MZ: Sees 3.4.1.3 as phase 2, would not want to hold up development  
GW: Formalized guidance would be important- is it the case that operations don't know what action they should take?   
CZ: Would be nice to have functionality. Operations group would have to do it?  
GW: Would be nice as long as adding was trivially easy.  
CONSENSUS: Guidance (3.4.1.3) is development priority 2

JG: This requirement is a member of a family relating to alarm "metadata"  
GW: General metadata suggests database design. 

GW: Following from the database,  couldn't documentation of schema accomplish 3.4.1.6? Should be phase 2  
EW: Should we provide client tools out of the box?  

WC: Is the vision that lclshome would change? If we have lclshome, don't really need the API  
MZ: Would not want the table structure leak into GUI  
CONSENSUS: API is development priority 2

MZ: Concerned that pain points are not represented by the requirements: syncing alarm IOC, config files, and displays    
GW: Suggests addition of requirement: Simplify the alarm maintenance workflow  
MZ: Automation of lclshome construction not easy  
GW: Instead, may be able to scan and look for alarms that have been modified  
JG: How would you validate this requirement is met?  
GW: Requirement met if had written script that searched config files and built report  
MZ: For pydm, lots of python code and no UI file whatsoever. Generating list of pvs from .py will be very difficult because embedded   in pieces in python code. Same case for EDM   
WC: It would have to be at runtime, also have to consider macros  

CONSENSUS: 3.4.1.11 is development priority 1

Requirement: 3.4.2.8, 3.4.2.9  
EW: Want to use ack on the pv itself  
WC: Was only thinking of LCLS when rating  
EW: Shantha does acknowledge  
GW: Should be useful for SPEAR and FACET  
CONSENSUS: 3.4.2.8, 3.4.2.9 are development priority 1

Requirement 3.4.2.10:  
WC: Assumption that new system will be sending messages to CMLOG, which already knows how to handle log filters   
MZ: Does not throttle well  
MZ: Has disabled ALH logging in some cases  
EW: The word optionally is potentially a problem. Should be able to turn off/on  
JG: Reword to: Optionally disable logging for an alarm.  
CONSENSUS: Do not need to support global disabling of logs. Single alarm disable is sufficient. Requirement is acceptable after rewording.  

Requirement 3.4.2.11:  
EW: Low dev priority  
MZ: Agrees  
GW: LDAP is a prerequisite  
MZ: Any reason we shouldn't just scrap this?   
GW: Requirement of the system- whether satisfied by another piece of software ancillary  
CONSENSUS: 3.4.2.11 development priority 2

Runtime requirements:  
WC: POV: coming into control room and asking to reboot   
GW: What does alarm deletion entail?  
EW: Delete alarm = stop subscription to the alarm state  
GW: Is this required only in a PAMM?  
MZ: No, some EIOCs let you reboot at will, variety of approaches and comfort  
GW: In terms of increase overall efficiency, may make sense to have runtime reconfiguration; but, not high priority  
MZ: What is exact meaning of runtime?  
EW: Runtime = while alarm server is running. Maybe should disable alarm group deletions in this case.  
MZ: Do changes persist when you make configuration changes?   
EW: Would need to solve in the general case, add save configuration method  
CONSENSUS: Runtime configurations are development priority 2

MZ: Budget question, does phase 2 mean never?  
WC: Budget would inform rankings  
EW: Suggest optimize based on stakeholder. Operations would have heavier use case- next case engineers  
GW: Notes that requirements don't necessarily need to be met by writing software  

ACTION ITEMS: Clean up document and circulate  
EW: Aim to submit document at end of week and send out for signiture. Emphasizes that important thing is not priority. Requirement inclusion is most important  

WC: Want to circle back to making things easier, maybe means inclusion of a pydm requirement  
EW: Configuring and maintaining should be covered  
GW: You say profide a configuration tool- schema validator is enough- xml editor   
EW: Should be covered by: Improve integration of the operator displays and the alarm system   
EW: Widgets need to be changed to be alarm aware. Once complete, have to modify displays to make alarm aware. 
MZ: Alarms should be property of each widget  
MZ: Recommends changing "expose" in 3.4.1.6 as suggests read-only   
GW: High level feature is straightforward: Streamlined maintenance of ALH, displays, and alarms of pvs  
NEXT STEPS: EW: MZ, WC, EW will try to nail down display integration requirement  
