# Extracting a single Frame JPG from Zmodo ZH-IXD15-WC

## This is just a script to extract a single jpg image from this IP stream

### This could be added to cron to grab it at regular intervals

```shell
nano grab_jpg.sh
```
Enter the Following in the script file to grab a single jpg frame

#!/bin/bash

host=XX.XX.XX.XX

date=$(date +"%Y-%m-%d_%H%M")

directory=/home/user

echo -e '\x55\x55\xaa\xaa\x00\x00\x00\x00\x00\x00\x00\x50' | netcat -w 2 $host 8000 |  avconv -i pipe:0 -y -q:v 9 -s 1280x720 -vframes 1 -r 1 $directory+$date.jpg 
