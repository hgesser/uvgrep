# uvgrep
UniVersal Grep (uvgrep)

The `uvgrep` tool lets you grep text, PDF, Microsoft Office (*docx*, *xlsx*, *pptx*) and LibreOffice/OpenOffice (ODF) files simultaneously. It requires that `bash` (for `getopts`), `grep`, `pdfgrep`, `sed`, `mktemp`, `xmllint`, and `unzip` (for unpacking *docx*, *xlsx*, *pptx*, *odt*, *odp* and *ods* files) are installed.

## Installation
Get the file `uvgrep`, make sure it is executable (`chmod a+x uvgrep`), and move it to a folder which is in the `PATH` variable, e. g. `/usr/local/bin`. Check that the required tools (see above) are installed.

## Usage
`uvgrep [options] [files]`

#### Options
`-i`: ignore case

`-n`: output line numbers (text) or page numbers (PDF)

`-x`: remove XML tags from output lines

#### Limitations
The current and initial version of `uvgrep` relies solely on filename extensions and should be modified to use the output of the `file` program. 

`uvgrep` cannot detect on which pages, tables or slides, of a LibreOffice document a search term was found; it cannot detect on which pages of a Microsoft Word document it was found. (However it will display information about slides or tables in Microsoft documents.)

`uvgrep` uses German error messages for the two problems that can occur (file not found, unsupported file type). In order to localize it, change the three message variables defined in the first lines.

#### Example

```
[esser@quad:~]$ uvgrep -in libreoffice *.sh *.pdf *.odt *.???x
uvgrep.sh:5:# uvgrep: grep txt, PDF and LibreOffice files
uvgrep.pdf:1:   5 # uvgrep: grep txt, PDF and LibreOffice files
test.odt:<text:p text:style-name="Standard">This test file contains the word "LibreOffice".</text:p>
test2.pptx[/slide9.xml]:<a:t>This is not a LibreOffice but a Microsoft Office file.</a:t>
[esser@quad:~]$ uvgrep -inx libreoffice *.sh *.pdf *.odt *.???x
uvgrep.sh:5:# uvgrep: grep txt, PDF and LibreOffice files
uvgrep.pdf:1:   5 # uvgrep: grep txt, PDF and LibreOffice files
test.odt:This test file contains the word "LibreOffice".
test2.pptx[/slide9.xml]:This is not a LibreOffice but a Microsoft Office file.
```

## Name Choice
`uvgrep` was meant to be named "ugrep" (universal grep), but a different project already uses that name, so I picked "uvgrep".

## Author and Copyright
Copyright (c) 2016-2022 Hans-Georg Eßer, licensed under the GPL version 3.
