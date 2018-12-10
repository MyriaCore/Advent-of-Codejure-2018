# Advent of Code 2018 Questions
Listed here, I'm going to document the actual problems found in the [2018 Advent of Code](https://adventofcode.com/2018/).

## Contents
- [Day 1](#day-1-chronal-calibration)
	- [Part 1](#day-1-part-1)
	- [Part 2](#day-1-part-2)
- [Day 2](#day-2-inventory-management-system)
	- [Part 1](#day-2-part-1)
	- [Part 2](#day-2-part-2)
- [Day 3](#day-3-no-matter-how-you-slice-it)
	- [Part 1](#day-3-part-1)
	- [Part 2](#day-3-part-2)

## Day 1: Chronal Calibration
### Day 1: Part 1
"We've detected some temporal anomalies," one of Santa's Elves at the Temporal Anomaly Research and Detection Instrument Station tells you. She sounded pretty worried when she called you down here. "At 500-year intervals into the past, someone has been changing Santa's history!"

"The good news is that the changes won't propagate to our time stream for another 25 days, and we have a device" - she attaches something to your wrist - "that will let you fix the changes with no such propagation delay. It's configured to send you 500 years further into the past every few days; that was the best we could do on such short notice."

"The bad news is that we are detecting roughly **fifty** anomalies throughout time; the device will indicate fixed anomalies with _stars_. The other bad news is that we only have one device and you're the best person for the job! Good lu--" She taps a button on the device and you suddenly feel like you're falling. To save Christmas, you need to get all _fifty stars_ by December 25th.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants _one star_. Good luck!

After feeling like you've been falling for a few minutes, you look at the device's tiny screen. "Error: Device must be calibrated before first use. Frequency drift detected. Cannot maintain destination lock." Below the message, the device shows a sequence of changes in frequency (your puzzle input). A value like `+6` means the current frequency increases by `6`; a value like `-`3`` means the current frequency decreases by 3.

For example, if the device displays frequency changes of `+1, -2, +3, +1`, then starting from a frequency of zero, the following changes would occur:

Current frequency  `0`, change of `+1`; resulting frequency  `1`.
Current frequency  `1`, change of `-2`; resulting frequency -`1`.
Current frequency -`1`, change of `+3`; resulting frequency  `2`.
Current frequency  `2`, change of `+1`; resulting frequency  `3`.
In this example, the resulting frequency is `3`.

Here are other example situations:

`+1, +1, +1` results in  `3`
`+1, +1, -2` results in  `0`
`-1, -2, -3` results in -`6`
Starting with a frequency of zero, **what is the resulting frequency** after all of the changes in frequency have been applied?

### Day 1: Part 2
You notice that the device repeats the same frequency change list over and over. To calibrate the device, you need to find the first frequency it reaches **twice**.

For example, using the same list of changes above, the device would loop as follows:

Current frequency  `0`, change of `+1`; resulting frequency ` 1`.
Current frequency  `1`, change of `-2`; resulting frequency `-1`.
Current frequency -`1`, change of `+3`; resulting frequency ` 2`.
Current frequency  `2`, change of `+1`; resulting frequency ` 3`.
(At this point, the device continues from the start of the list.)
Current frequency ` 3`, change of ` +1`; resulting frequency ` 4`.
Current frequency ` 4`, change of ` -2`; resulting frequency ` 2`, which has already been seen.
In this example, the first frequency reached twice is `2`. Note that your device might need to repeat its list of frequency changes many times before a duplicate frequency is found, and that duplicates might be found while in the middle of processing the list.

Here are other examples:

- `+1, -1` first reaches `0` twice.
- `+3, +3, +4, -2, -4` first reaches `10` twice.
- `-6, +3, +8, +5, -6` first reaches `5` twice.
- `+7, +7, -2, -7, -4` first reaches `14` twice.

**What is the first frequency your device reaches twice?**

## Day 2: Inventory Management System
### Day 2: Part 1
You stop falling through time, catch your breath, and check the screen on the device. "Destination reached. Current Year: 1518. Current Location: North Pole Utility Closet 83N10." You made it! Now, to find those anomalies.

Outside the utility closet, you hear footsteps and a voice. "...I'm not sure either. But now that so many people have chimneys, maybe he could sneak in that way?" Another voice responds, "Actually, we've been working on a new kind of suit that would let him fit through tight spaces like that. But, I heard that a few days ago, they lost the prototype fabric, the design plans, everything! Nobody on the team can even seem to remember important details of the project!"

"Wouldn't they have had enough fabric to fill several boxes in the warehouse? They'd be stored together, so the box IDs should be similar. Too bad it would take forever to search the warehouse for **two similar box IDs...**" They walk too far away to hear any more.

Late at night, you sneak to the warehouse - who knows what kinds of paradoxes you could cause if you were discovered - and use your fancy wrist device to quickly scan every box and produce a list of the likely candidates (your puzzle input).

To make sure you didn't miss any, you scan the likely candidate boxes again, counting the number that have an ID containing **exactly two of any letter** and then separately counting those with **exactly three of any letter**. You can multiply those two counts together to get a rudimentary [checksum](https://en.wikipedia.org/wiki/Checksum) and compare it to what your device predicts.

For example, if you see the following box IDs:
- abcdef contains no letters that appear exactly two or three times.
- bababc contains two a and three b, so it counts for both.
- abbcde contains two b, but no letter appears exactly three times.
- abcccd contains three c, but no letter appears exactly two times.
- aabcdd contains two a and two d, but it only counts once.
- abcdee contains two e.
- ababab contains three a and three b, but it only counts once.
- Of these box IDs, four of them contain a letter which appears exactly twice, and three of them contain a letter which appears exactly three times. Multiplying these together produces a checksum of 4 * 3 = 12.

**What is the checksum** for your list of box IDs?

### Day 2: Part 2
Confident that your list of box IDs is complete, you're ready to find the boxes full of prototype fabric.

The boxes will have IDs which differ by exactly one character at the same position in both strings. For example, given the following box IDs:
- `abcde`
- `fghij`
- `klmno`
- `pqrst`
- `fguij`
- `axcye`
- `wvxyz`

The IDs `abcde` and `axcye` are close, but they differ by two characters (the second and fourth). However, the IDs `fghij` and `fguij` differ by exactly one character, the third (`h` and `u`). Those must be the correct boxes.

**What letters are common between the two correct box IDs?** (In the example above, this is found by removing the differing character from either ID, producing `fgij`.)

## Day 3: No Matter How You Slice It
### Day 3: Part 1
The Elves managed to locate the chimney-squeeze prototype fabric for Santa's suit (thanks to someone who helpfully wrote its box IDs on the wall of the warehouse in the middle of the night). Unfortunately, anomalies are still affecting them - nobody can even agree on how to **cut** the fabric.

The whole piece of fabric they're working on is a very large square - at least `1000` inches on each side.

Each Elf has made a **claim** about which area of fabric would be ideal for Santa's suit. All claims have an ID and consist of a single rectangle with edges parallel to the edges of the fabric. Each claim's rectangle is defined as follows:
- The number of inches between the left edge of the fabric and the left edge of the rectangle.
- The number of inches between the top edge of the fabric and the top edge of the rectangle.
- The width of the rectangle in inches.
- The height of the rectangle in inches.
- A claim like `#123 @ 3,2: 5x4` means that claim ID `123` specifies a rectangle `3` inches from the left edge, `2` inches from the top edge, `5` inches wide, and `4` inches tall. Visually, it claims the square inches of fabric represented by `#` (and ignores the square inches of fabric represented by `.`) in the diagram below:

```
...........
...........
...#####...
...#####...
...#####...
...#####...
...........
...........
...........
```
The problem is that many of the claims **overlap**, causing two or more claims to cover part of the same areas. For example, consider the following claims:
```
#1 @ 1,3: 4x4
#2 @ 3,1: 4x4
#3 @ 5,5: 2x2
```
Visually, these claim the following areas:
```
........
...2222.
...2222.
.11XX22.
.11XX22.
.111133.
.111133.
........
```
The four square inches marked with `X` are claimed by **both `1` and `2`**. (Claim `3`, while adjacent to the others, does not overlap either of them.)

If the Elves all proceed with their own plans, none of them will have enough fabric. **How many square inches of fabric are within two or more claims?**

### Day 3: Part 2

Amidst the chaos, you notice that exactly one claim doesn't overlap by even a single square inch of fabric with any other claim. If you can somehow draw attention to it, maybe the Elves will be able to make Santa's suit after all!

For example, in the claims above, only claim `3` is intact after all claims are made.

**What is the ID of the only claim that doesn't overlap?**