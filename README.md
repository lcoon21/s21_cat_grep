# s21_cat & s21_grep

## General info 

Implementation of GNU `cat` and BSD `grep` with all major flags and flags combinations.

## Goal & requirements

The goal of this project was to learn & replicate the functionality of the GNU cat & 
BSD grep, including all major flags and their combinations. There must be integration tests
that compare original programs with our versions.

## Key learnings
- Working with regular expressions in C
- Files IO in C
- grep / cat usage knowledge
- PCRE syntax
- Working with `argv / argc`, CLI args parsing

## Build

```
$ git clone git@github.com:lcoon21/s21_cat_grep.git
$ cd repo/src/
$ make
```

## s21_cat

### s21_cat Usage

`$ s21_cat [OPTION] [FILE]...`

### s21_cat Options

| No. | Options | Description |
| ------ | ------ | ------ |
| 1 | -b (GNU: --number-nonblank) | numbers only non-empty lines |
| 2 | -e implies -v (GNU only: -E the same, but without implying -v) | but also display end-of-line characters as $  |
| 3 | -n (GNU: --number) | number all output lines |
| 4 | -s (GNU: --squeeze-blank) | squeeze multiple adjacent blank lines |
| 5 | -t implies -v (GNU: -T the same, but without implying -v) | but also display tabs as ^I  |

### s21_cat integration tests

s21_cat not fully replicates original GNU cat functionality, it includes all flags but not flags combinations. 

Integration tests are launched via bash script 'test.sh'. Before launching tests s21_cat executable must be built.

```
$ bash cat/test.sh
```

<div align="center"><img src="assets/s21_cat_sample.png"></div>
<div align="center"><sub>s21_cat usage example</sub></div>

## s21_grep

### s21_grep Usage

`s21_grep [option] template [file_name]`

### s21_grep Options

| No. | Options | Description |
| ------ | ------ | ------ |
| 1 | -e | pattern |
| 2 | -i | Ignore uppercase vs. lowercase.  |
| 3 | -v | Invert match. |
| 4 | -c | Output count of matching lines only. |
| 5 | -l | Output matching files only.  |
| 6 | -n | Precede each matching line with a line number. |
| 7 | -h | Output matching lines without preceding them by file names. |
| 8 | -s | Suppress error messages about nonexistent or unreadable files. |
| 9 | -f file | Take regexes from a file. |
| 10 | -o | Output the matched parts of a matching line. |

### s21_grep integration tests:

s21_grep replicated major BSD grep (2.5.1-FreeBSD) flags without their combinations listed above. s21_grep uses PCRE syntax and regex engine provided by the developers of `regex.h`.

Integration tests are launched via bash script 'test.sh'. Before launching tests s21_grep executable must be built.

```
$ bash grep/test.sh
```
