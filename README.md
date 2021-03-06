# pdfxplr

Extract hidden data from pdf files.

### Summary

This script attempts to extract potentially interesting data from pdf files, that might be useful in penetration tests, forensics analysis or OSINT investigations.
Besides classic metadata, it searches for elements usually overlooked, including metadata inside embedded images, paths on the operating system, usernames, software components.

### Prerequisites

You will need Python 3 with the following libraries:
* chardet
* pdfminer.six
* python-dateutil
* Pillow

To install them, after cloning the repository, simply run:
```
pip3 install -r requirements.txt
```

### Configuration

The list of exif metadata that will be extracted is set in utils.py, as well as the list of character encodings that will be tried when all else fails.

### Usage

```
pdfxplr.py v. 0.1 - Find hidden data in pdf
by sowdust

usage: pdfxplr.py [-h] [-m] [-a] [-e] [-l] [-i] [-u] [-s] [-p] [-x] [-v]
                  [--encoding encoding] [--store-images path]
                  PATH

extract interesting data from pdf files.

positional arguments:
  PATH                 path to a file or folder

optional arguments:
  -h, --help           show this help message and exit
  -m, --metadata       show metadata, off by default
  -a, --all            show all, add -m to show also metadata
  -e, --email          list all email addresses
  -l, --links          list all URLs
  -i, --ips            list all IP addresses
  -u, --usernames      list all usernames
  -s, --software       list all software components identified
  -p, --paths          list all content found in image alt fields (ie. system
                       paths)
  -x, --images         extract info from images, use -m to show metadata
  -v, --verbose        verbose mode
  --encoding encoding  input document encoding
  --store-images path  path to store extracted images (optional)
```

It is possible to test the script using the sample pdf file in the "sample" folder. 

### Acknowledgments

Thanks to Gianluca Baldi for the help with the old version of this project and to Maurizio Agazzini for having suggested using the images' alt text in pdf files.

The XMP metadata parser is by Matt Swain (http://blog.matt-swain.com/post/25650072381/a-lightweight-xmp-parser-for-extracting-pdf).

Some regexes are from John Gruber (http://daringfireball.net/2010/07/improved_regex_for_matching_urls).

Dumppdf is a slightly modified version from the original tool shipped with pdfminer (https://github.com/pdfminer/pdfminer.six/blob/master/tools/dumppdf.py)

