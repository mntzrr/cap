# cap: copy-and-paste

If you want to copy your files and directories but don't know yet the destination, cap (copy-and-paste) lets you flag them and then paste them into your current working directory.

## Installation

```bash
git clone https://gitlab.com/montazar/cap.git
sudo cp cap/cap /usr/local/bin
```

## Manual

You flag files and directories (“items”) by running `cap` without any options, passing each item as an argument. For example, if you want to flag everything in your current working directory:

```bash
cap *
```

You can list flagged files and directories using the `--list` (or shorthand `-l` ) option. Each item is associated with an index. The index is used for selecting the item you want to paste in the current working directory using the `-p` option.

```bash
cap -p 5
```

 If you omit the index, the most recently flagged or pasted item (whichever occurred most recently) will be pasted. That is, index 1.

```bash
cap -p
```

The pasted item will be moved to index 1 in the list. This way, you don’t have to remember the index if you want to copy the same item to multiple directories. Simply run the above command again, or even shorter:

```bash
cap
```

You can clear the list by running `--clear` (or shorthand `-C`).



```
CAP(1)                                                                                User Commands                                                                                CAP(1)

NAME
       cap - flag files and directories for copy

SYNOPSIS
       cap [OPTION] [FILE...]

DESCRIPTION
       Flag any files and directories and paste in current working directory.

OPTIONS
       -l, --list
              list all flagged

       -a, --all
              paste all flagged

       -p [INDEX]
              paste only most recently flagged or a specific item in the list

       --clear
              clear all flagged

       -h, --help
              print this manual

EXAMPLES
       cap *  
        	  flag everything in current directory for copy

       cap -p 
       		  paste most recently flagged

       cap -p 5
              paste the 5th entry in the list

       cap --all
              paste all flagged files and directories

cap 1.0.0                                                                             November 2020                                                                                CAP(1)

```

