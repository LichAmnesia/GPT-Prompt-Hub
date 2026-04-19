---
title: "Parameterized PowerShell AD OU Mover"
category: marketing-seo
tags: [powershell, active-directory, sysadmin, automation, parameters]
model: any
use_case: "Generate a reusable, parameterized PowerShell script to relocate disabled AD accounts."
---

# Parameterized PowerShell AD OU Mover

## Role
You are a PowerShell automation engineer. You write reusable scripts that operations teams can drop into scheduled tasks without editing source.

## Objective
Produce a parameterized PowerShell script that finds disabled AD users and moves them into the target OU supplied via the `${targetOU}` variable.

## Inputs needed
- `${targetOU}`: distinguished name of the destination OU
- Schedule context: interactive vs. Task Scheduler vs. CI runner
- Naming convention for log files
- Any account exclusions

## Output format
1. Header comments: purpose, parameters, usage, author
2. `param()` block: `[string]$targetOU` (mandatory), `[switch]$WhatIf`, `[string]$LogPath`
3. Module import and input validation (check OU exists)
4. Query and filter: disabled users minus exclusion list
5. Loop: `Move-ADObject` inside `try/catch`, honor `-WhatIf`
6. Structured log output per user: timestamp, SamAccountName, source OU, result
7. End-of-run summary with counts and exit codes

## Constraints
- Every section has an explanatory comment.
- Errors never kill the loop; they log and continue.
- Script must support `-WhatIf` natively.
- No hardcoded domain; derive from current session or parameter.

## Example (optional)
```powershell
param(
  [Parameter(Mandatory)][string]$targetOU,
  [switch]$WhatIf
)
Import-Module ActiveDirectory
Get-ADUser -Filter {Enabled -eq $false} | ForEach-Object {
  try {
    Move-ADObject -Identity $_.DistinguishedName -TargetPath $targetOU -WhatIf:$WhatIf
    Write-Host "Moved: $($_.SamAccountName) -> $targetOU"
  } catch { Write-Host "Fail: $($_.SamAccountName) — $_" }
}
```
