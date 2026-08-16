OverTheWire: Bandit — Level 8 → Level 9
Level 8 → Level 9
Goal

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

Concept

This level is about spotting a unique line in a large file full of near-duplicate lines. Doing it by eye is impractical, so we lean on two classic Unix text-processing tools:

sort — arranges lines alphabetically/numerically. This matters because uniq (below) only detects duplicates that are adjacent to each other, not duplicates scattered throughout a file. Sorting groups identical lines together.
uniq -u — after sorting, this filters output to show only the lines that are not repeated (-u = "unique"). Lines that appear more than once are dropped entirely.

So the pipeline is: sort the file so identical lines sit next to each other, then ask uniq to print only the lines that have no duplicate neighbor.

Command
bash
sort data.txt | uniq -u
Why this works

sort does the heavy lifting of grouping, and uniq -u does a single linear pass afterward comparing each line only to the one before it — which is why the sort step isn't optional. If you skip it, uniq -u will miss duplicates that aren't next to each other and give you a wrong (too-long) result.
