# PMD for IBM
Documentation and examples of KAJA's IBM driver variant for OPL soundcards

## Setup

1. Go to Delmunsoft.com and follow the [PMD setup steps 1 and 3](http://delmunsoft.com/PMD%20Setup.html)
2. Get PMDIBM.COM from this repository and place it in your PMD driver directory with the other things

## Use

1. Write your MML, using OPL2 type patches for FM
2. Open DOSBOX and type PMDIBM to load the PMD drivers into DOSBOX's emulator
3. Compile directly in DOSBOX, either specifying options in the command line or including them in the preprocessor commands (`#OPTION /L /V`)
4. Using `pmp [directory of compiled .M]`, you can play your file directly in DOSBOX

## OPL-type patches for PMD

```
; NM AG FB		E.Bass
@00  0  2		=HDBass1
; AR DR RR SL TL KSL ML KSR EGT VIB AM
 12, 9,12, 2, 4, 0, 0, 0, 1, 0, 0
 15, 5, 6, 1, 0, 0, 1, 0, 0, 0, 0
```

Patches for this driver are two operators, with an ADR envelope, keyscale level and rate, vibrato and amplitude modulation flags and only two algorithms. OPL is noticeably less flexible than OPN for the same kinds of tasks, and you'll note levels on channel output are noticeably lower.

There is no SSG, as OPL is FM only with 9 2-operator FM channels (ABCDEFGHI). the `#TEMPO` preprocessor command doesn't seem to do anything, but the `#TIMER` one does, and it seems to be the kind of multiplier seen in KOLIN2 as it's a clock timer byte.

Using the example songs [MUS1](http://chipmusic.org/NoyemiK/music/nocturnal-affair-title-dos-opl2) and [AD_HD1](), you can get a basic idea of how the differences stack up to the OPN variants, and it is easier to use and test with less extra stuff involved (such as dedicated outside players or drivers).
