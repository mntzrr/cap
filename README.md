# cap: copy-and-paste

If you want to copy your files and directories but don't know yet the destination, cap (copy-and-paste) lets you flag them and then paste them into your current working directory.

## Installation

```bash
git clone https://gitlab.com/montazar/cap.git
cd cap
sudo cp cap /usr/local/bin
chmod 644 _cap

# Bash/ZSH completion
if ! [ -d "$ZSH/completions" ]; then
	mkdir "$ZSH/completions"
fi

cp _cap "$ZSH/completions"
sudo cp _cap /usr/share/bash-completion/completions
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

You can clear the list by using the  `--clear` option (or shorthand `-C`), or if you want to unflag a specific item in the list only, use the `-d INDEX` option.

```bash
cap -d 5
```

You can also unflag from a **range** using the same option.

```bash
cap -d 5-10
```

Unflags all items from the 5th index to the 10th (inclusive).

```bash
cap -d 5-
```

Unflags all items, starting from the 5th index and higher.



```
CAP(1)                                                                                User Commands

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

       -p [INDEX|RANGE]
              paste recently flagged, a specific item in the list or all items within a range

       -d [INDEX|RANGE]
              unflag recently flagged, a specific item from the list or all items within a range

       -C, --clear
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

       cap -p 7-9
              paste all items from the 7th to 9th (inclusive) index

       cap --all
              paste all flagged files and directories

       cap -d 7-
              unflag all items from the 7th index and higher (inclusive)

cap 1.5.2                                                                             February 2021
```

## Uninstall

```bash
sudo rm /usr/local/bin/cap
rm "$ZSH/completions/_cap"
sudo rm /usr/share/bash-completion/completions/_cap
```

