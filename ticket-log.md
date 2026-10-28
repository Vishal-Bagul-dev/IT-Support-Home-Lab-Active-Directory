# Helpdesk Ticket Log

Mock tickets created and resolved in my `techlab.local` lab. Each ticket was reproduced in the lab and fixed. Add your own screenshot name in the last column after you test each one.

| Field | Meaning |
|---|---|
| Priority | Low / Medium / High |
| Time | Time taken to resolve (fill in your real time) |

---

## Summary Table

| ID | Category | Issue | Priority | Time | Status |
|---|---|---|---|---|---|
| T-001 | Account | User forgot password | Medium | 5 min | Resolved |
| T-002 | Account | User account locked out | High | 5 min | Resolved |
| T-003 | Account | New employee setup | Medium | 15 min | Resolved |
| T-004 | Account | Employee left, disable account | Medium | 5 min | Resolved |
| T-005 | Account | User deleted by mistake | High | 10 min | Resolved |
| T-006 | Access | Cannot open shared folder | High | 10 min | Resolved |
| T-007 | Access | User needs access to HR folder | Medium | 10 min | Resolved |
| T-008 | Network | PC cannot join the domain | High | 15 min | Resolved |
| T-009 | Network | No internet / network on client | High | 10 min | Resolved |
| T-010 | Network | Cannot ping server | Medium | 10 min | Resolved |
| T-011 | Printer | Printer not showing on PC | Medium | 10 min | Resolved |
| T-012 | Printer | Print jobs stuck in queue | Medium | 5 min | Resolved |
| T-013 | Hardware/OS | PC running slow | Low | 15 min | Resolved |
| T-014 | Policy | USB drive should be blocked | Medium | 15 min | Resolved |
| T-015 | Policy | Password rejected as too weak | Low | 5 min | Resolved |

---

## Ticket Details

### T-001: User forgot password
- **Reported by:** Rahul (Sales)
- **Problem:** Cannot log in, forgot password.
- **Cause:** User forgot password.
- **Fix:**
  1. Open Active Directory Users and Computers.
  2. Find the user, right-click, then **Reset Password**.
  3. Enter a temporary password meeting complexity rules.
  4. Tick **User must change password at next logon**.
  5. Verify the user can log in.
- **KB article:** KB-01

### T-002: User account locked out
- **Reported by:** Priya (HR)
- **Problem:** "Account is locked" message at login.
- **Cause:** Too many wrong password attempts.
- **Fix:**
  1. Open the user's Properties, then the **Account** tab.
  2. Tick **Unlock account**, then Apply.
  3. Ask the user to log in with the correct password.
- **KB article:** KB-02

### T-003: New employee setup
- **Reported by:** HR manager
- **Problem:** New joiner needs an account and access.
- **Cause:** New hire.
- **Fix:**
  1. Create the user in the correct OU.
  2. Set a temporary password with change-at-next-logon.
  3. Add the user to the department group.
  4. Log in on the client PC to confirm shared drive and printer work.
- **KB article:** KB-03

### T-004: Employee left, disable account
- **Reported by:** HR manager
- **Problem:** Former employee's account must not be usable.
- **Cause:** Employee resigned.
- **Fix:**
  1. Right-click the user, then **Disable Account**.
  2. Remove from groups if required by company policy.
  3. Move the user to a "Disabled Users" OU.
  4. Do not delete immediately; keep for audit.
- **KB article:** KB-04

### T-005: User deleted by mistake
- **Reported by:** IT lead
- **Problem:** A user account was deleted accidentally.
- **Cause:** Human error.
- **Fix:**
  1. Enable the AD Recycle Bin (Active Directory Administrative Center).
  2. Open the **Deleted Objects** container.
  3. Right-click the user, then **Restore**.
  4. Check group membership and password.
- **KB article:** KB-05

### T-006: Cannot open shared folder
- **Reported by:** Amit (Sales)
- **Problem:** "Access denied" opening `\\DC01\SalesShare`.
- **Cause:** User not in the Sales group.
- **Fix:**
  1. Check the folder's Sharing and Security permissions.
  2. Add the user to `Sales-Team`.
  3. Ask the user to log off and on again, then retest.
- **KB article:** KB-06

### T-007: User needs access to HR folder
- **Reported by:** Priya (HR)
- **Problem:** Needs access to the HR shared folder.
- **Cause:** Access not yet granted.
- **Fix:**
  1. Get manager approval.
  2. Add the user to `HR-Team`.
  3. Confirm access, then close the ticket.
- **KB article:** KB-06

### T-008: PC cannot join the domain
- **Reported by:** IT team
- **Problem:** "Domain could not be found" when joining.
- **Cause:** Client DNS was not pointing to the server.
- **Fix:**
  1. Set the client's preferred DNS to `192.168.10.1`.
  2. Test with `nslookup techlab.local`.
  3. Retry the domain join with `TECHLAB\Administrator`.
- **KB article:** KB-07

### T-009: No internet / network on client
- **Reported by:** Rahul (Sales)
- **Problem:** PC shows no network.
- **Cause:** Network adapter disabled or wrong IP.
- **Fix:**
  1. Check the adapter is enabled.
  2. Run `ipconfig /all` and check the IP.
  3. Run `ipconfig /release`, then `ipconfig /renew`, or correct the static IP.
  4. Test with `ping 192.168.10.1`.
- **KB article:** KB-08

### T-010: Cannot ping server
- **Reported by:** IT team
- **Problem:** Ping to `192.168.10.1` times out.
- **Cause:** Windows Firewall blocking ICMP, or VMs on different virtual networks.
- **Fix:**
  1. Confirm both VMs use the same Internal Network name.
  2. Enable "File and Printer Sharing (Echo Request ICMPv4-In)" on the server.
  3. Retest the ping.
- **KB article:** KB-08

### T-011: Printer not showing on PC
- **Reported by:** Priya (HR)
- **Problem:** Shared printer is missing.
- **Cause:** Printer not connected on this PC.
- **Fix:**
  1. Open **Settings, Printers & scanners, Add device**.
  2. Add using `\\DC01\PrinterName`.
  3. Print a test page.
- **KB article:** KB-09

### T-012: Print jobs stuck in queue
- **Reported by:** Amit (Sales)
- **Problem:** Documents will not print and stay in the queue.
- **Cause:** Print Spooler is stuck.
- **Fix:**
  1. Open `services.msc`.
  2. Restart **Print Spooler**.
  3. Cancel stuck jobs and print again.
- **KB article:** KB-09

### T-013: PC running slow
- **Reported by:** Rahul (Sales)
- **Problem:** Computer is very slow.
- **Cause:** Too many startup programs and low disk space.
- **Fix:**
  1. Open Task Manager and check CPU, memory and disk.
  2. Disable unnecessary startup apps.
  3. Run Disk Cleanup.
  4. Restart and compare performance.
- **KB article:** KB-10

### T-014: USB drive should be blocked
- **Reported by:** Security manager
- **Problem:** Staff must not copy data to USB drives.
- **Cause:** Company policy.
- **Fix:**
  1. Open Group Policy Management.
  2. Create a GPO linked to the target OU.
  3. Enable **All Removable Storage classes: Deny all access**.
  4. Run `gpupdate /force` on the client and test.
- **KB article:** KB-11

### T-015: Password rejected as too weak
- **Reported by:** New employee
- **Problem:** "Password does not meet requirements."
- **Cause:** Password did not meet complexity rules.
- **Fix:**
  1. Explain the rules: minimum length, and 3 of 4 character types.
  2. Choose a stronger password, for example `Welcome@2026`.
- **KB article:** KB-01
