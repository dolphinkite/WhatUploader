# WhatUploader
Python script to scan a music folder that contains FLAC rips of CDs, transcode them to mp3 (320,v2,v0), create torrent files and upload them to What.

Here is a list of the intended specifications for this project. Create a Python 3 script that will:

- Scan a given folder that contain a FLAC rip of a CD. This folder may contain:
	- Properly named and tagged .flac files
	- A scan of the cover of the album (file can either be names cover.jpg. Cover.jpg, front.jpg, Front.jpg or simply anyname if there is only one .jpg file present
	- [Optional] a .cue and .log file
	- subfolders for each disc, named Disc 1, Disc 2, etc.
	- A metadata.txt file that contains metadata associated with the album and that will help upload a complete description to What.cd
	- The typical directory name should look like : Artist - Album (year) [FLAC]. For example: Max-A-Million - Take Your Time (1995) [FLAC]
	- If this is a compilation, the artist should be "Various Artists"
	
- For  a given directory, all files should be transcoded to the mp3 formats specified in the medata.txt (which can be a combinaison of 320, V0 or V2) and stored in a newly created directory with the appropriate name
- Once the files have been transcoded, a .torrent file will be created (unless excluded as a command line option) for each directory. That .torrent will contain your personal What.cd announce url so you should be careful with whom you share that file
- Upload the newly created torrent file, pulling the complimentary information (such as catalogue number, tags, etc.) from metadata.txt and including them in the upload page of What.cd. This also mean uploading the cover.jpg (or other) file to imgur (or whatimg) and linking to it
- Allow for a simulation option and generate a log file that contains:
	- What folder/files would be trancoded
	- A list of what would be the newly created folders/mp3 files
	- A list of the missing tags that would prevent proper upload (year, artist, etc.)
	- A list of missing or misconfigured properties in metadata.txt (for example, torrent type not specified, no tags, etc.)

- This script must support the uploading of ebooks, with a description contained in the metadata. 

A copy of a sample metadata.txt has been added to this project. Unicode and accentuated characters must absolutely be supported throughout the project (in folder names, file names and tags).

Command line arguments:
Usage: python WhatUploader.py [-credentials userPassFile.txt] [-createTorrent torrentOutputDirectory] [-verbose] [-simulation] inFolder 

-credential: Specify a text file that will contain your What.cd username on the first line and your password on the second line
-createTorrent: Specify that .torrent files should be created and where the .torrent should be stored. If not specified, no .torrent will be created, nor uploaded
-verbose: Will output detailed information
-simulation: Run through each files and create a log file of what WOULD be created should the command be run
inFolder: Specify on which folder this script should be run

Additional future options:
- Scan a folder that contains FLAC subfolders
- Specify which formats to be added

Note: This script will NOT check if that torrent already exist on the site. This should be done manually beforehand.
