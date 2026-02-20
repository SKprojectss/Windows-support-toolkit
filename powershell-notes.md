# PowerShell Notes - Trobleshooting basics

---
## 1. Check top CPU usage 

**Command:**
Get-Process | Sort-Object CPU -Descending | Select-Object -First 5

**What it does:**
Shows the processes using the most CPU time.

**Note:** *CPU column shows total processor time used, not real-time percentage.*

**Why it matters:**
High CPU usage can slow down the system.

**When would I use this:**
If a user comes telling me their computer is slow and/or applications are not responding properly.

---
## 2. Check top RAM usage

**Command:**
Get-Process | Sort-Object WS -Descending | Select-Object -First 5 Name, WS

**What it does:**
Shows the processes using the most working memory (RAM).

**Note:** *WS (Working Set) represents the amount of physical memory currently used by the process.*

**Why it matters:**
Low available RAM can cause performance issues.

**When would I use this:**
When I've checked the CPU's performance if the computer is still not respondin properly,
I'll check RAM because it might be the other issue that's slowing the computer down.

---
## 3. Check Windows Update service

**Command:**
Get-Service wuauserv

**What it does:**
Shows status of Windows Update service.

**Why it matters:**
Stuck updates can impact the system performance.

**When would I use this:**
For the next step I would check the windows update service if nothing comes up with CPU and RAM.

## 3.1 Check Windows Update service StartType

**Command:**
Get-Service wuauserv | Select-Object Status, StartType

**What it does:**
Shows the start type of Windows Update service.

**Note:** *Service may be Stopped and still normal if StartType is Manual.*

---
## 4. Check disk space

**Command:**
Get-PSDrive -PSProvider FileSystem

**What it does:**
Displays available and used space on drives.

**Note:** *10% free space rule. Keeping at least 10-20% free disk space helps maintain system performance 
and allows Windows to handle updates properly*

**Why it matters:**
Low disk space can affect performance and updates.

**When would I use this:**
I have checked CPU, RAM and updates and the computer is still not responding properly, I'll lastly check disk space.
Sometimes there might be applications using disk space eventhough the application is not needed from that we can get free usage space for the user.

---
