# SPEAR Walkthrough

Attendees: Shantha Condamoor, Jackie Garrahan, Ernest Williams

The purpose of this meeting is to review the use of the alarm handler by SPEAR, get a sense of how this differs from use at the LCLS, and to review SPEAR's templating scheme for IOC development.

## Notes

### General
* SPEAR ALH is stuck at old version of EPICS-base 3.14.11
* Main deterrent for update is the customization  
    * Tied in with email notfication system and annunciations
* Alarm system info is integrated with display at SPEAR. This is not automated and must be manually configured.
* Tree depth is typically limited to three levels
* Stephanie Allison had begun moving towards an LCLS-style home display at the request of Peter 
* SPEAR embeds acknowledgment widgets into their displays
* Alarms come not just from EPICS but also compiled MATLAB programs 
* Ticket numbers are associated with bypasses every time
* Window integrated with screen to open during drill-down
* Channel Watcher and ALH are discrete systems at SPEAR

### Event log
* SPEAR event log uses color coding based on type of alarm transition
* Accepts messages from softIOC, console, matlab, etc.
* Has filtering capability
* Tied to email notification system + audible alarming

### ALH config
* Use the ALARMCOUNTFILTER in ALH config files for message filters
* Shantha has seen use of masks beyond nolog and ack
* SPEAR makes heavy use of "internal"- ASG set to sting "internal" as to not clobber the alarm system

### Alarm tools
* Found at: /afs/slac/g/spear/vol6/tools/AlarmConfigsTop
* Distinct set of tools from LCLS
* All tracked in CVS

### Takeaways
* IMPORTANT CONSIDERATION FOR NGAS: What are list of runtime requirements vs the static configuration?
Can mask be changed at runtime?


### Substitutions
* Application: /afs/slac/g/spear/epics/app/ALARMS/alhPVApp
* DB files:
    * monitorStatus.db
    * monitor.db