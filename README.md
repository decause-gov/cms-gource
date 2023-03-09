# cms-gource

This repository contains configuration scripts, log files, and graphic assets
used to generate a source code repository visualization using [Gource](https://gource.io).

For more information on how to use [CMS.gov](https://cms.gov)'s collection of
APIs, datasets, frameworks, and style guides to develop applications that help
people get the services and benefits they rely on, visit
[developer.cms.gov](https://developer.cms.gov).

## Usage
1. install dependencies
2. create repos directory
3. clone repos
4. generate logs
5. insert names
6. colorize logs
7. Concatenate and sort logs
8. run gource 
9. export video

### Install Dependencies 

The author used the open source [Homebrew](https://brew.sh) project to install
the gource and ffmpeg tools on a Mac. 

    brew install gource
    brew install ffmpeg


Gource and ffmpeg can also be installed directly from source on
[GitHub.com](https://github.com/acaudwell/Gource) and
[ffmpeg.org](https://ffmpeg.org/download.html#get-sources) or via most Linux
distribution package managers.

Author used standard commandline tools such as the [Vim text
editor](https://www.vim.org) to add hexadecimal color codes to the end of each
line in the log to colorize the output, and the [sed stream
editor](https://www.gnu.org/software/sed/) to insert parent names into logs.
Most text manipulation tools capable of regular expressions or find-and-replace
functions should work to achieve the same results.

### Create repos directory

    mkdir repos 
    cd repos


### Clone Repos

    git clone https://github.com/CMSgov/ab2d.git
    git clone https://github.com/CMSgov/bcda-app.git
    git clone https://github.com/CMSgov/beneficiary-fhir-data.git
    git clone https://github.com/CMSgov/bluebutton-web-server.git
    git clone https://github.com/CMSgov/dpc-app.git
    git clone https://github.com/CMSgov/design-system.git


### Generate Logs

    gource --output-custom-log log1.txt repos/ab2d
    gource --output-custom-log log2.txt repos/bcda-app
    gource --output-custom-log log3.txt repos/beneficiary-fhir-data
    gource --output-custom-log log4.txt repos/bluebutton-web-server
    gource --output-custom-log log5.txt repos/dpc-app
    gource --output-custom-log log6.txt repos/design-system

### Insert Names

    sed -i -r -E "s#(.+)\|#\1|/ab2d#" log1.txt
    sed -i -r -E "s#(.+)\|#\1|/bcda#" log2.txt
    sed -i -r -E "s#(.+)\|#\1|/beneficiary-fhir-data#" log3.txt
    sed -i -r -E "s#(.+)\|#\1|/blue-button#" log4.txt
    sed -i -r -E "s#(.+)\|#\1|/dpc#" log5.txt
    sed -i -r -E "s#(.+)\|#\1|/design-system#" log6.txt

### Colorize Logs (using vim)

    vim log1.txt
    :%norm A|F0F0F0

    vim log2.txt
    :%norm A|136A5D

    ...


### Concatenate and Sort Logs

    APIs only
    cat log1.txt log2.txt log3.txt log4.txt log5.txt | sort -n > cmsapis.log

    APIs + design-system
    cat log1.txt log2.txt log3.txt log4.txt log5.txt log6.txt | sort -n > cmsapis-plusdesign.log

    APIs + QPP quality tools
    cat log1.txt log2.txt log3.txt log4.txt log5.txt log7.txt log8.txt | sort -n > cmsapis-plusqpp.log



### Run Gource Visualization

    APIs Only
    time gource --load-config cms.conf -f -1920x1080 cmsapis.log 

    API + design-system
    time gource --load-config cms.conf -f -1920x1080 cmsapis-plusdesign.log 

(last output: 131.51s user 6.60s system 33% cpu 6:51.33 total)

### Export Video (.webm or .mp4)

    gource --load-config cms.conf -1920x1080 cmsapis.log -f -o - | ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i - -vcodec libvpx -b 10000K cms-gource.webm

    gource --load-config cms.conf -1920x1080 cmsapis.log -f -o - | ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i - -vcodec libx264 -preset ultrafast -pix_fmt yuv420p -crf 1 -threads 0 -bf 0 cms-gource.mp4


## LICENSE
As a work of the United States Government, this project is in the
public domain within the United States.

Additionally, we waive copyright and related rights in the work
worldwide through the CC0 1.0 Universal public domain dedication.

### CC0 1.0 Universal Summary
This is a human-readable summary of the [Legal Code (read the full
text)](https://creativecommons.org/publicdomain/zero/1.0/legalcode).

### No Copyright
The person who associated a work with this deed has dedicated the work to
the public domain by waiving all of his or her rights to the work worldwide
under copyright law, including all related and neighboring rights, to the
extent allowed by law.

You can copy, modify, distribute and perform the work, even for commercial
purposes, all without asking permission.

### Other Information
In no way are the patent or trademark rights of any person affected by CC0,
nor are the rights that other persons may have in the work or in how the
work is used, such as publicity or privacy rights.

Unless expressly stated otherwise, the person who associated a work with
this deed makes no warranties about the work, and disclaims liability for
all uses of the work, to the fullest extent permitted by applicable law.
When using or citing the work, you should not imply endorsement by the
author or the affirmer.

## Acknowledgments

CMS would like to thank [General Services Administration](https://gsa.gov)
(GSA)’s [18F](https://18f.gsa.gov) team, the [Consumer Financial Protection
Bureau](https://cfpb.gov) (CFPB), and the [Office of Management and
Budget](https://www.whitehouse.gov/omb/) (OMB) for their inspirational work in
the use of Free/Open Source Software in the Federal Government.

Author would like to give special thanks Andrew Caudwell and the
[https://Gource.io](https://Gource.io) Project contributors. Source code
repository available at
[https://github.com/acaudwell/Gource](https://github.com/acaudwell/Gource)
