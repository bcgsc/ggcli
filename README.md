# Description

Plot TSV data with ggplot from the command line.

# Caveats

* Currently hardcoded to do `geom_line()` plots
* Doesn't do multi-part plots

# Usage

	Plot TSV data with ggplot from the command line.

	Usage: ggcli [-x COLNAME] [-y COLNAME] [-t TITLE] [-o OUTPUT] [-c COLNAME] [TSV_FILE]

	Options:
	   -x COLNAME                  TSV column to use for x coords [default: x]
	   -y COLNAME                  TSV column to use for y coords [default: y]
	   -c COLNAME --color COLNAME  assign colors by COLNAME
	   -o FILE --output FILE       output file (defaults to STDOUT)
	   -t TITLE --title TITLE      title for plot [default: title]

# Dependencies

* R (statistics program)
* R packages: `docopt`, `ggplot2`

Note: I was initially getting some error about a non-existent `regex` function in the `stringr` package. Installing the latest version of `stringr` fixed it.

# Examples

test.tsv:

	foo	bar	group
	1	1	a
	2	2	a
	3	3	b
	4	4	b

Plot using STDIN/STDOUT:
	
	$ ggcli -x foo -y bar -t mytitle test.tsv > plot.pdf
	$ ggcli -x foo -y bar -t mytitle test.tsv -o plot.pdf
	$ cat test.tsv | ggcli -x foo -y bar -t mytitle > plot.pdf
	
Send plot directly to ImageMagick's `display` program:

	$ ggcli -x foo -y bar -t mytitle test.tsv | display

Plot multiple groups (with different colors):

	$ ggcli -x foo -y bar -t mytitle -c group test.tsv > plot.pdf
