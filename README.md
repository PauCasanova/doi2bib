# doi2bib

*doi2bib*, or *d2b* for short, is a simple shell script that serves as a BibTeX citations manager.

When you provide a PDF file or a DOI number, the script extracts the DOI, queries [https://crossref.org](https://crossref.org) for bibliography information, and downloads the BibTeX entry corresponding to the associated literature to a .bib file of your choosing.

In one command, you have just gathered every bibliographic information available about that article into one organized file.

## Installation

### Prerequisites

Because this is a Bash script, it is preferred to use Linux and macOS. If you are a Windows user, you can set up your system to run shell scripts by following [this guide](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/), or use [Cygwin](https://www.cygwin.com/).

At the minimum, you will need `pdfinfo` and `pdftotext` installed on your device. If you are running a Linux distribution or Windows Subsystem for Linux, it should already be installed. If you are running macOS or Windows, you can download prebuilts of the xpdf command line tools from [here](https://www.xpdfreader.com/download.html).

### Getting the Script

If you are familiar with git, or would like to [get git](https://git-scm.com/downloads), the easiest way to download this script to your device is with:

```
$ git clone https://gitlab.com/maister/doi2bib.git
```

However, if "git" just looks like a funny word to you, you can download this script using the download button left of the blue "Clone" buttons in the upper right corner of this page. Then, extract the file using your favorite file extractor.

## Usage

First, move the file named `d2b` into the folder where your PDF articles are stored. Then, open your terminal application and type:

```
$ cd path/to/your/directory/
```

where `path/to/your/directory/` is replaced with the path to your PDF folder.

**Note**: you do not type the `$`.

Then, run the script like so:

```
$ ./d2b article.pdf file.bib
```

where `article.pdf` and `file.bib` are replaced with your article you want to cite and your BibTeX file, respectively.

If no BibTeX entry was extracted for your article, open the PDF and find the DOI number. Then, run the script with the number in place of the file name, like so:

```
$ ./d2b 10.doi.number file.bib
```

where `10.doi.number` and `file.bib` are replaced with the DOI of the article and your BibTeX file, respectively.

Confused? Watch this GIF below.

### See It In Action

![](preview.gif)

## Advanced Usage

Say you have a folder *full* of PDF articles. You can use this script to get BibTeX entries for the entire directory in two simple commands like so:

```
$ cd path/to/your/directory/
$ for x in *.pdf
$ do
$ ./d2b "$x" "file.bib"
$ done
```

where `path/to/your/directory` and `file.bib` are replaced with the folder where your PDF articles are stored and the name of your bibliography file, respectively. This will run the script on every PDF file and gather the bibliography information into `file.bib`.

Remember to double check your file to ensure that a BibTeX entry is found for every article. If there is an error in the DOI extraction, search for the DOI number yourself and run the script with the number instead of the filename.

### See It In Action

![](preview_multi.gif)

## License

This script is licensed under [MIT](LICENSE.md). Thank you to [Conner McDaniel](https://www.youtube.com/watch?v=nO4T8JDNYG0) for the idea.
