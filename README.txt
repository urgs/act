# act
shell command line activity tracker by threads

simple file based structure with aliases se rc_act 
try the HOWTO at the end of this file - just for fun - 

------------ # activity --------------------------------------------------------------
.ah
------------ # activity --------------------------------------------------------------

------------ # activity --------------------------------------------------------------
.an  s1 s2 ..              - new activity for backlog - continue working on old task
.ai  s1 s2 ..              - new activity interrupt current activity 
.aib s1 s2 .. @@ s3 s4 ..  - new activity interrupt below activity described by s1 s2 ... 
.af  [s1 s2 .. ]           - activity finished - wthout param use current activity
.ala                       - list active activities in threads see also .aqt and .aqti 
.alb                       - list backlog activities 
.asb s1 s2 ..              - start activity from backlog
.as2 s1 s2 ..              - switch to new activity
.arm s1 s2 ..              - rm/delete activity from system 
------------ # info files ------------------------------------------------------------
.ani s1 s2                 - new action info file for action 
.ali                       - list info files for actions created with .ani
.alif                      - list info files for actions created with .ani full path
------------ # threads --------------------------------------------------------------
.ant  [name]               - new thread - new chain 
.alt  [thr]                - list threads not finished activities
.alts                      - list threads by name
.alta [thr]                - list threads all entries 
------------ # query   --------------------------------------------------------------
.aqt                       - query threads simple view
.aqti                      - query threads status info 
------------ # archiving ------------------------------------------------------------
.aat  [thr]                - archive thread see .aqt or .alt 
.aatc [thr]                - archive thread - clean up competed tasks only
.aaa "time stamp"          - archive activity use ts from .ala 
.aab "time stamp"          - archive activity use ts from .alb 
------------ # misc -----------------------------------------------------------------
.ah                        - this help
ACT_DEBUG=ON               - enables additional output
SYS_ACT_DIR_HOME           - overwrites ACT_DIR_HOME default $HOME/act 

-------------
HOWTO mini :
-------------
A.) run rc_act in the current shell or at login ( optional set environment SYS_ACT_DIR_HOME )
    . rc_act
B.) initialze once 
    .ainit

C.) create some action for backlog 
    .an action001 some text
    .an action002 some text
    .an action003 some text
    .an action003 another  text
    .an action004 some text

D.) check your backlog 
   .alb

E.) check your current threads
   .alt

F.) create a thread 
   .ant today

E.) start processing an activitie from backlog
   .asb action004              # the first word is sufficient task coud be indentified
   .asb action003 another      # there are mutliple activities with action003, see C
   
F.) interrupt your current activity by solving an importend problem (e.g L2 support)
   .ai importent activity a-001
   # check
   .alt
   .ala
   # other interruptions:
   .ai importent activity a-002
   .ai importent activity a-003
   .ai importent activity a-004
   # check
   .alt
   # you are working on a-004 suddently a-002 become most important
   .as2 a-002              # you can also use the timestamp from .alt
   # check
   .alt
   .ala
   # a-002 is done /finished
   .af 
   # check
   .alt
   .ala
   # check and see also completed
   .alta
   # you get the information that a-003 become obsolet
   .af a-003
   # check
   .alt
   .ala

G.) you can remove/archive a complete thread, it makes sense to switch to another thread before
    with .as2 ..... or create a new on with .ant 
    and not removing the current active thread.
    .aat thr-today
   
...... play arround, try other things ....
...... rm -rf ~/act    # delete all traces
...... repeat (B)
...... have fun 








