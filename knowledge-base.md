# Knowledge Base

Short, repeatable fix guides for common IT support problems in the `techlab.local` lab.

| ID | Article |
|---|---|
| KB-01 | Reset a user password / password rules |
| KB-02 | Unlock a locked account |
| KB-03 | Create a new user |
| KB-04 | Disable a user account |
| KB-05 | Restore a deleted user |
| KB-06 | Give a user access to a shared folder |
| KB-07 | Join a PC to the domain |
| KB-08 | Fix network / ping problems |
| KB-09 | Fix printer problems |
| KB-10 | Speed up a slow PC |
| KB-11 | Block USB storage with Group Policy |

---

## KB-01: Reset a user password / password rules

**Symptoms:** User forgot password, or a new password is rejected.

**Steps:**
1. Open **Active Directory Users and Computers**.
2. Find the user, right-click, then **Reset Password**.
3. Enter a temporary password and tick **User must change password at next logon**.

**Default password rules:** at least 7 characters, with 3 of 4 types (uppercase, lowercase, number, symbol), and not containing the username.

**Example of a valid password:** `Welcome@2026`

---

## KB-02: Unlock a locked account

**Symptoms:** "The referenced account is currently locked out."

**Steps:**
1. Open the user's **Properties**, then the **Account** tab.
2. Tick **Unlock account**, then click **Apply**.
3. Ask the user to retry with the correct password.

---

## KB-03: Create a new user

**Steps:**
1. In Active Directory Users and Computers, right-click the correct OU, then **New, User**.
2. Enter name and logon name, then set a temporary password.
3. Tick **User must change password at next logon**.
4. Open the user's **Member Of** tab and add the department group.
5. Test by logging in on a client PC.

---

## KB-04: Disable a user account

**Steps:**
1. Right-click the user, then **Disable Account**.
2. Move the user to a "Disabled Users" OU.
3. Delete only after the retention period set by company policy.

---

## KB-05: Restore a deleted user

**Steps:**
1. Open **Active Directory Administrative Center** and enable the **Recycle Bin** (do this before incidents happen; it cannot be undone).
2. Open the **Deleted Objects** container.
3. Right-click the user, then **Restore**.
4. Verify groups, OU and password status.

---

## KB-06: Give a user access to a shared folder

**Steps:**
1. Confirm approval from the manager.
2. Add the user to the right security group (for example `Sales-Team`).
3. Ask the user to log off and on again so the new group applies.
4. Test by opening `\\DC01\FolderName`.

**Tip:** Give permissions to groups, not to individual users.

---

## KB-07: Join a PC to the domain

**Steps:**
1. Set the client's preferred DNS to the server IP (`192.168.10.1`).
2. Test with `ping 192.168.10.1` and `nslookup techlab.local`.
3. Press `Win + R`, type `sysdm.cpl`, then **Change**, choose **Domain**, and enter `techlab.local`.
4. Log in with `TECHLAB\Administrator` and restart.

**Note:** Windows Home cannot join a domain. Use Pro or Enterprise.

---

## KB-08: Fix network / ping problems

**Steps:**
1. Check the network adapter is enabled.
2. Run `ipconfig /all` and confirm IP and DNS are correct.
3. Run `ipconfig /release` and `ipconfig /renew` if using DHCP.
4. Run `ping 192.168.10.1` to test the server.
5. If ping fails, check both VMs use the same Internal Network name and that the firewall allows ICMP echo.

---

## KB-09: Fix printer problems

**Printer missing:**
1. Open **Settings, Printers & scanners, Add device**.
2. Choose **Add manually** and enter `\\DC01\PrinterName`.
3. Print a test page.

**Jobs stuck in queue:**
1. Press `Win + R`, type `services.msc`.
2. Restart **Print Spooler**.
3. Clear stuck jobs and print again.

---

## KB-10: Speed up a slow PC

**Steps:**
1. Open Task Manager and check which process uses most CPU, memory or disk.
2. Disable unneeded startup apps (Task Manager, **Startup** tab).
3. Run **Disk Cleanup** and free disk space.
4. Restart the PC and check again.

---

## KB-11: Block USB storage with Group Policy

**Steps:**
1. Open **Group Policy Management**.
2. Create a new GPO and link it to the target OU.
3. Edit it: **Computer Configuration, Policies, Administrative Templates, System, Removable Storage Access**.
4. Enable **All Removable Storage classes: Deny all access**.
5. On the client, run `gpupdate /force` and test with a USB drive.
