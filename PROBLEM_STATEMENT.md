# Problem Statement

## OVERVIEW

- **Track**: T-05 SODE — SOC & Offensive Detection Engineering
- **Difficulty Level**: High (Sigma specification implementation, real-time server-side log matching, Monaco Editor
integration, 5 gamified detection challenges)
- **Tech Domain**: Detection Engineering, Sigma Rules, YAML, Python/FastAPI, pySigma, Monaco Editor, React, Windows
Security Logs
- **Expected Deliverable**: A browser-based Sigma rule authoring and validation lab with a Monaco Editor, a 3-dataset
log library, a real-time matching engine, and 5 scored detection-engineering challenges. 


## DESCRIPTION

Sigma is the universal standard for portable detection rules across SIEM platforms, and writing Sigma rules is a critical
skill gap for junior SOC analysts — yet no platform offers an interactive, gamified Sigma authoring environment.
This problem statement asks teams to build a Sigma Rule Builder with live, server-side rule matching against curated
log datasets and 5 gamified detection-engineering challenges with automated scoring. 

## OBJECTIVES

- Integrate a Monaco Editor configured with Sigma YAML syntax highlighting and autocompletion.
- Build a Sigma parser and structural validator backend using pySigma or a custom implementation of the
Sigma specification.
- Build a simulated log dataset library: Windows Security Event Logs (4624, 4625, 4688, 4698, 7045), Sysmon
logs, and Web Access logs, each with benign and malicious entries.
- Build a real-time rule-matching engine (POST /run-rule) returning matched entries, match count, and a falsepositive-rate estimate within 3 seconds.
- Build 5 Detection Engineering Challenges with reference answer rules (e.g. Pass-the-Hash, Scheduled Task
Creation, LSASS Access, Encoded PowerShell, SQL Injection) scored on precision, recall, and false-positive
rate. 

## EXPECTATIONS

### For Participants (Hackathon Teams):

- Use Python/FastAPI with pySigma for parsing; Monaco Editor is mandatory (not CodeMirror or any other
editor).
- Keep log matching strictly server-side, returning results within 3 seconds.
- Use only synthetic log datasets containing known-malicious patterns matching each challenge's target
technique.
- Ensure full Sigma spec compliance: condition logic, selection modifiers (contains, endswith, re), and
detection field structures.
- Expose POST /validate-rule, POST /run-rule, GET /log-datasets, and GET /challenges, and ship via dockercompose up.

## EXPECTED RESULTS

### Evaluation Focus:

- Sigma Spec Compliance — tested against known-correct Sigma rules for condition logic and modifiers.
- Matching Accuracy — tested against rules with known ground-truth match sets.
- Monaco Editor Quality and Detection Challenge Design are assessed for professional polish and educational
soundness.
- Working PoC Demo — write a rule live, select a dataset, run it, view matches, and see the challenge scored,
with no cached results.

### PWNDORA Product Integration Alignment:

- Detection engineering is the fastest-growing specialisation in blue-team cybersecurity; a Sigma rule builder
positions PWNDORA as a premier destination for detection-engineering upskilling in India.

> **Bonus Extension (Optional)**: Build a 'Rule Transpiler' that converts a validated Sigma rule to Splunk SPL and Microsoft
Sentinel KQL.

