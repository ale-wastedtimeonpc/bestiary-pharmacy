# bestiary-pharmacy

The pharmacy of the [Wasted Time on PC bestiary](https://wastedtimeonpc.com/bestiario): small read-only checks born
from the failures of a home server that runs a local AI, 24/7.

Every monster the bestiary records gets a **vaccine**: a check that would find it if it came back.
Here are the ones that are useful outside that one machine. Each is a single file: download it, read it, run it.

| vaccine | against | how to use |
|---|---|---|
| [`chi_legge`](chi_legge) | **species n° 3, [The reader you didn't look at](https://wastedtimeonpc.com/specie-03)**: what you write for one reader (a name, a line in a file, a file in a folder) is also read by another, and the failure shows up there | `./chi_legge <word-or-path> [folders]` lists the scripts, services, timers and cron jobs that name it. Run it before changing something shared, keep the list, compare it after the change |
| [`reset_reason`](reset_reason) | **the reset without a single line**: an AMD mini-PC that restarts in an instant, with nothing in the log | `./reset_reason` lists every reset reason the chipset recorded (as printed by the kernel at each boot) and marks the unwanted ones; exit code 1 if there is one |

And one rule from species n° 3 that needs no tool: **a check that looks for a process by name must not be able to find
itself.** `while pgrep -f tcpdump …` inside a script that contains the word `tcpdump` waits forever, because it finds
its own command line. Write the pattern so it does not match itself: `pgrep -f '[t]cpdump'`.

More vaccines (species n° 1 and n° 2) will come when they work on more than one machine.

MIT license. Read-only by design: none of these change anything.

---

*Ale — wastedtimeonpc.com*
