# mediam

Mediam (media maid) is a tools made to help to prune, classify, purge, etc. your multi-media files like images and videos.

#Usage
/usr/bin/mediam -h -R -r -c <HIERARCHY> -a <ACTION> [source] [target]

Arguments:
-r  --rename                Rename files with the date taken using format yyMMdd_hhmmss.
-R  --recursive             Execute action(s) recursively.
-c  --classify=HIERARCHY    Classify the images according the specified TYPE.
-a  --action=ACTION         Action type. Could be 'copy', 'move' or 'link'.
-v  --verbose               Display details while executing actions.
-d  --debug                 Display more details while executing actions.
-h  --help                  Display this help and exit.


HIERARCHY
Hrearchy of classification. Possible to specifiy several formats or levels.
If separated by slash (/) then generate folders.
Ex: year-month/type => create directories for each years-month, and then inside a directory for each type.
    > 2010-12/image
    > 2011-01/video
Possible values are:
    year: create a directory for each years of media.
    month: create a directory for each months of media.
    day: create a directory for each days of media.
    media: create a directory for each type of media (image or video)
    country: create a directory for each country. Try to get it from google services according GPS coordinate in EXIF.
    state: create a directory for each country. Try to get it from google services according GPS coordinate in EXIF.
    city: create a directory for each city. Try to get it from google services according GPS coordinate in EXIF.
    type: create a directory for each type of media (video or image).


ACTION
Action to do while classifying. Default is 'copy'.
    copy: make a copy of media in new classification structure.
    move: move the file in new classification structure.
    link: create a symbolic link of media in the new classification structure.
