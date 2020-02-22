# doi2bib

*doi2bib*, or *d2b* for short, is a simple shell script that serves as a BibTeX citations manager.

When you provide a PDF file or a DOI number, the script extracts the DOI, queries [https://crossref.org](https://crossref.org) for bibliography information, and download the BibTeX entry corresponding to the associated literature to a .bib file of your choosing.

In one command, you have just gathered every bibliographic information available about that article into one organized file.

## Installation

### Prerequisites

Because this is a shell script, it is preferred to be used on Linux and macOS devices. If you are a Windows user, you can quickly set up your system to run shell scripts by following [this guide](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) and downloading the "Ubuntu" Windows Subsystem for Linux from the Microsoft Store.

Then, at the bare minimum, you will need `poppler` installed on your device. If you are running a Linux distribution or Windows Subsystem for Linux, it should already be installed. If you are running macOS, follow [this guide](http://macappstore.org/poppler/) to get poppler on your device.

### Getting the Script

If you are familiar with git, or would like to [get git](https://git-scm.com/downloads), the easiest way to download this script to your device is with:

```
$ git clone https://gitlab.com/maister/doi2bib.git
```

However, if "git" just looks like a funny word to you and you're tired of getting another program, you can download this script the traditional way using the download button between the "Find file" and the blue "Clone" button in the upper right corner of this page. Then, extract the file using your favorite file extractor.

## Usage

Open your terminal application and type:

```
$ cd path/to/your/directory/
```

where `path/to/your/directory/` is replaced with the path to your where your PDF articles are stored.

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

Say you have a folder full of PDF articles. You can use this script to get BibTeX entries for the entire directory in two simple commands like so:

```
$ cd path/to/your/directory/
$ for x in *.pdf
$ do
$ ./d2b "$x" "file.bib"
$ "done"
```

### See It In Action

![](preview_multi.gif)


where `path/to/your/directory` and `file.bib` are replaced with the folder where your PDF articles are stored and the name of your bibliography file, respectively. This will run the script *d2b* on every PDF file and gather the bibliography information into `file.bib`.

Please double check your file to ensure that a BibTeX entry is found for every article. If there is an error in the DOI extraction, search for the DOI number yourself and run the script with the number instead of filename.