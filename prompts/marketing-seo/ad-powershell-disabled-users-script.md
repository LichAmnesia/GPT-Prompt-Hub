---
title: "PowerShell AD Cleanup: Move Disabled Users to OU"
category: marketing-seo
tags: [powershell, active-directory, sysadmin, automation]
model: any
use_case: "Generate a logged, error-handled PowerShell script that sweeps disabled AD users into a designated OU."
---

# PowerShell AD Cleanup: Move Disabled Users to OU

## Role
You are a Windows systems administrator. You write production-ready PowerShell scripts for Active Directory housekeeping, with full error handling and audit logging.

## Objective
Produce a PowerShell script that queries AD for all disabled user accounts and moves them to a specified Organizational Unit, with robust logging and safe failure modes.

## Inputs needed
- Target OU distinguished name (e.g., `OU=DisabledUsers,DC=example,DC=com`)
- Domain and privileged account context
- Logging path and rotation policy
- Optional exclude list (service accounts, VIP accounts, etc.)
- Dry-run flag preference (default on?)

## Output format
1. Script header with purpose, author, version, change log
2. Parameter block (`CmdletBinding`, `param`) with `-TargetOU`, `-LogPath`, `-DryRun`, `-ExcludeFile`
3. Module import with guard (`Import-Module ActiveDirectory`)
4. Pre-flight checks: OU exists, caller has Move-ADObject rights
5. Query block: `Get-AD User -Filter {Enabled -eq $false}` with exclude filter applied
6. Move loop with `try/catch`, per-user log line, and summary counters
7. Final summary: moved count, skipped count, errors, log file path
8. Example invocation lines (dry-run and live)

## Constraints
- Default to `-DryRun $true`. Require explicit flag to perform moves.
- Log every action to a timestamped file, one line per user.
- Never hardcode credentials; use current session or `Get-Credential`.
- Handle missing OU, permission-denied, and RODC scenarios gracefully.

## Example (optional)
```powershell
Import-Module ActiveDirectory
$TargetOU = "OU=DisabledUsers,DC=example,DC=com"
Get-ADUser -Filter {Enabled -eq $false} | ForEach-Object {
  try { Move-ADObject -Identity $_.DistinguishedName -TargetPath $TargetOU }
  catch { Write-Warning "Skip $($_.SamAccountName): $_" }
}
```
