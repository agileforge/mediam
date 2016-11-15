# mediam
Mediam (media maid) is a tools made to help to renam, classify, prune, etc. your multi-media files like images and videos.

## Prerequisit
Before using mediam, check that exiftool and jq are installed on your system.
* **exiftool**             http://www.sno.phy.queensu.ca/~phil/exiftool/
* **jq**                   https://stedolan.github.io/jq/
* **imagemagick**          http://www.imagemagick.org/script/index.php

`sudo apt-get install exiftool`

`sudo apt-get install jq`

`sudo apt-get install imagemagick`

## Commands
Available commands are "rename", "classify" and "prune".

### Command rename

Use it to rename all media files (images and video) in a directory in a standard date time 
format yyyymmdd_HHMMSS. This allow to order the files chronologicaly. MediaM gets the date 
time taken found in EXIF informations.

You cand do it recursively with option -R . 

Ex: `mediam rename -R /path/of/your/medias`

### Command classify

Use it to classify your media files (images and video) in a given hierarchy.

Ex: `mediam classify -R -a link -h year/month/type /path/to/your/media /target/path
