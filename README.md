# mediam
Mediam (media maid) is a tools made to help to rename, classify, prune, etc. your multi-media files like images and videos.

## Prerequisit
Before using mediam, check that following packages are installed on your system.
* **exiftool**             http://www.sno.phy.queensu.ca/~phil/exiftool/
* **jq**                   https://stedolan.github.io/jq/
* **imagemagick**          http://www.imagemagick.org/script/index.php

```{r, engine='bash', count_lines}
sudo apt-get install exiftool jq imagemagick
```

## Commands
Available commands are "rename", "classify" and "prune".

### Command rename
Use it to rename all media files (images and video) in a directory in a standard date time 
format yyyymmdd_HHMMSS. This allow to order the files chronologicaly. MediaM gets the date 
time taken found in EXIF informations.

You cand do it recursively with option -R . 

Ex: `mediam rename -R /path/of/your/medias`

### Command classify
Use it to classify your media files (images and video) in a given hierarchy. You can classify by copying, moving or linking (`-a` option).

With option `-h` you can specify the hierarchy to use. If the separator is `/`, it will create a directory for each hierarchy level.

Ex: `-t year-month/country` will create directories per year-month (2011-12), then sub directories by county.

#### Possible hierarchy
* **year** 
* **month**
* **day**
* **type** Type of media (image or video).
* **country** Country where the image has been taken if GPS coordinates found.
* **city** City where the image has been taken if GPS coordinates found.

Ex: `mediam classify -R -a link -h year-month/type /path/to/your/media /target/path`

### Command prune
Prune is used to remove redundant pictures dur to intensive shooting. It will try to detect similarity between images in order of time.

A prune process is made in three times.

1. Recognition of similar images. This will create a directoriy per type of similar images and put link to similar images inside. Ex: `mediam prune /path/to/your/media /target/prune/path`
1. Selection of images to delete. Just remove links in prune directories of images that have to be deleted. 
1. Commit. This will synchronize your deletion choice in the source directory. Ex: `mediam prune -c /target/prune/path`
