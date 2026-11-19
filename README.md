# bestiary-pharmacy

The pharmacy of the [Wasted Time on PC bestiary](https://wastedtimeonpc.com/bestiario): small read-only checks born
from the failures of a home server that runs a local AI, 24/7.

Every monster the bestiary records gets a **vaccine**: a check that would find it if it came back.
Here are the ones that are useful outside that one machine. Each is a single file: download it, read it, run it.

| vaccine | against | how to use |
|---|---|---|
| [`chi_legge`](chi_legge) | **species n° 3, [The reader you didn't look at](https://wastedtimeonpc.com/specie-03)**: what you write for one reader (a name, a line in a file, a file in a folder) is also read by another, and the failure shows up there | `./chi_legge <word-or-path> [folders]` lists the scripts, services, timers and cron jobs that name it (text references only: a path built at run time, or a reader outside the folders it scans, is not found). Run it before changing something shared, keep the list, compare it after the change |
| [`reset_reason`](reset_reason) | **the reset without a single line**: an AMD mini-PC that restarts in an instant, with nothing in the log | `./reset_reason` lists every reset reason the chipset recorded (as printed by the kernel at each boot) and marks the unwanted ones; exit code 1 if there is one, 2 if it cannot say (no reset lines, or reasons it does not recognise) |
| [`righe_ripetute`](righe_ripetute) | **the stuck reader**: a vision model, asked to transcribe photos of pages, got stuck twice and repeated the same line 508 and 469 times in a row; the next model answered on top of those broken transcriptions as if they were real | `./righe_ripetute <folder> [--hours H] [--min N]` lists the text files (transcripts, OCR, model outputs) changed in the last hours where one line repeats N+ times in a row (blank lines skipped); names and counts only; exit code 1 if there is one, 2 if it cannot check or checked nothing (`--empty-ok` to accept an empty window) |
| [`mai_piu`](mai_piu) | **the fallback that comes back**: a self-hosted AI assistant that, when its translation service returned nothing, quietly fell back to a local model that improvised; the fix removed the fallback on that path | `./mai_piu <log> "<forbidden text>" ["<start line>"]` counts the lines with the old text only after the LAST start of the service; exit code 1 if it is back, 2 if it cannot check |

And one rule from species n° 3 that needs no tool: **a check that looks for a process by name must not be able to find
itself.** `while pgrep -f tcpdump …` inside a script that contains the word `tcpdump` waits forever, because it finds
its own command line. Write the pattern so it does not match itself: `pgrep -f '[t]cpdump'`.

More vaccines (species n° 1 and n° 2) will come when they work on more than one machine.

MIT license. Read-only by design: none of these change anything.

---

*Ale — wastedtimeonpc.com*
