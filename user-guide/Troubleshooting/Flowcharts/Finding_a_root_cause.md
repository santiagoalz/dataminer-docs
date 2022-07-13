---
uid: Finding_a_root_cause
---

# Finding a root cause

<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
<script>
    mermaid.initialize({ startOnLoad: true });
</script>
<div class="mermaid">
    sequenceDiagram
        participant Alice
        participant Bob
        Alice->>John: Hello John, how are you?
        loop Healthcheck
            John->>John: Fight against hypochondria
        end
        Note right of John: Rational thoughts <br/>prevail!
        John-->>Alice: Great!
        John->>Bob: How about you?
        Bob-->>John: Jolly good!    
</div>
<div class="mermaid">
graph TD

%% Define styles %%

classDef classTerminal fill:#1e5179,stroke:#1e5179,color:#ffffff,stroke-width:0px;
classDef classDecision fill:#4baeea,stroke:#4baeea,color:#ffffff,stroke-width:0px;
classDef classExternalRef fill:#9ddaf5,stroke:#9ddaf5,color:#1E5179,stroke-width:0px;
classDef classActionClickable fill:#999999,stroke:#999999,color:#ffffff,stroke-width:0px;
classDef classAction fill:#dddddd,stroke:#dddddd,color:#1E5179,stroke-width:0px;
classDef classSolution fill:#58595b,stroke:#58595b,color:#ffffff,stroke-width:0px;

%% Define blocks %%
START([Find the root cause])
Investigate([Where to start?])
CheckStartup{{Does the DMA start up?}}
CHECK1{{Any critical issues? }}
identify{{Identify issue per... }}
DatabaseFlowcharts{{Is it a database problem?}}
WhichDb{{Which database?}}

DMAStartupIssues([To DMA Startup &lt;br>Issues flowchart])
critical([To Critical Issues &lt;br>flowchart])

ProcessFlowcharts([Process])

Cassandra([Cassandra])

%% Connect blocks %%

START --> CheckStartup

CheckStartup -->|Yes| CHECK1
CheckStartup --> |No| DMAStartupIssues

CHECK1 --> |Yes| critical
CHECK1 ---> |No| DatabaseFlowcharts

DatabaseFlowcharts -->|Yes|WhichDb
DatabaseFlowcharts --->|No|identify 

identify --> ProcessFlowcharts

WhichDb --> Cassandra

%% Define hyperlinks %%
     click CHECK1 "https://community.dataminer.services/troubleshooting-finding-a-root-cause/#critexamples" "examples of critical issues"
	 click critical "/troubleshooting-critical-issues-overview/" "To critical issues flowchart"
	 click DMAStartupIssues "/troubleshooting-dataminer-start-up-issues/" "DMA Startup Issues"
	 click ProcessFlowcharts "/troubleshooting-process-identification/" "Process identification"
	 click WhichDb "https://community.dataminer.services/troubleshooting-finding-a-root-cause/#whichdb" "Identify the Database"
	 click Cassandra "https://community.dataminer.services/troubleshooting-cassandra/" "Troubleshooting Cassandra"
     click Investigate "/documentation/troubleshooting-where-to-start/" "Where to start investigating?"

%% Apply styles to blocks %% 

class START classTerminal; 
class WhichDb,DatabaseFlowcharts,CheckStartup,CHECK1,identify classDecision;
class Investigate,Cassandra,DMAStartupIssues,critical,ProcessFlowcharts classExternalRef;
</div>
