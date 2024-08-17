---
title: "PowerShell Force Compliance Baseline Evaluation"
created: 2021-03-03
date: 2021-03-03
categories: 
  - sccm
  - windows-10
tags: 
  - baseline
  - command-line
  - compliance
  - powershell
  - sccm
authors: 
  - thecd
description: "Forcing a SCCM compliance rule is easy to do but you may not know how. This guide explains how PowerShell can be used to force this."
---

SCCM Compliance rule evaluation for a new rule can sometimes be slow or maybe you just need to manually evaluate compliance baselines or rules on a machine or group of machines.

Regardless of your reasoning, the PowerShell script below can help you achieve the goal of manually and remotely kicking off SCCM compliance rule evaluations.

To make this reusable in the future, we will create a simple function that we can call along with a hostname to do the dirty work for us.

```
function Invoke-ForceEvaluation
{
    param (
        [Parameter(Mandatory=$true, HelpMessage="Computer Name",ValueFromPipeline=$true)] $ComputerName
           )
    $Baselines = Get-WmiObject -ComputerName $ComputerName -Namespace root\ccm\dcm -Class SMS_DesiredConfiguration
    $Baselines | % { ([wmiclass]"\\$ComputerName\root\ccm\dcm:SMS_DesiredConfiguration").TriggerEvaluation($_.Name, $_.Version) }
}
foreach($hostname in (Get-Content C:\path to our txt file with hostnames)) {
    Invoke-ForceEvaluation $hostname
}
```

If you need to call it on a single machine, you can take out the foreach loop and call the function by itself passing a single hostname.

To clarify, this script will evaluate every baseline that is assigned to the target machine. Ensure that you know what baselines are going to run prior to running this to avoid unexpected results.

If you'd like to know more about SCCM or how to do something that I haven't covered, please let me know in the comments.
