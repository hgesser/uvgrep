# uvgrep
UniVersal Grep (uvgrep)

The `uvgrep` tool lets you grep text, PDF and LibreOffice/OpenOffice (ODF) files simultaneously. It requires that `bash` (for `getopts`), `grep`, `pdfgrep`, `sed`, `xmllint`, and `unzip` (for unpacking *odt*, *odp* and *ods* files) are installed.

## Usage
`pdfgrep [options] [files]`

## Options
`-i`: ignore case

`-n`: output line numbers (text) or page numbers (PDF)

## Limitations
The current and initial version of `uvgrep` relies solely on filename extensions and should be modified to use the output of the `file` program. 

`uvgrep` cannot detect on which pages of an ODF document a search term was found.

## Name Choice
`uvgrep` was meant to be named "ugrep" (universal grep), but a different project already uses that name, so I picked "uvgrep".
