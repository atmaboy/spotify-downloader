# Spotify-Downloader

- Downloads songs from YouTube in an MP3 format by using Spotify's HTTP link.

- Can also download a song by entering its artist and song name (in case if you don't have the Spotify's HTTP link for some song).

- Automatically fixes song's meta-tags which include:

  - Title
  - Artist
  - Album
  - Album art
  - Album artist
  - Genre
  - Track number
  - Disc number
  - Release date
  - and some more..

- Works straight out of the box and does not require to generate or mess with your API keys.

<br>

That's how your Music library will look like!

<img src="http://i.imgur.com/Gpch7JI.png" width="290"><img src="http://i.imgur.com/5vhk3HY.png" width="290"><img src="http://i.imgur.com/RDTCCST.png" width="290">

## Reporting Issues

- Search for your problem in the [issues section](https://github.com/Ritiek/spotify-downloader/issues?utf8=%E2%9C%93&q=) before opening a new ticket. It might be already answered and save us time :D.

- Provide as much information possible when opening your ticket.

## Installation & Usage

<img src="http://i.imgur.com/Dg8p9up.png" width="600">

- This version supports both Python2 and Python3.

- Note: `play` and `lyrics` commands have been deprecated in the current brach since they were not of much use and created unnecessary clutter. You can still get them back by using `old` branch though.

### Debian, Ubuntu, Linux & Mac

```
cd
git clone https://github.com/ritiek/spotify-downloader
cd spotify-downloader
pip install -U -r requirements.txt
```

You'll also need to install FFmpeg for conversion (use `--avconv` if you'd like to use that instead):

Linux: `sudo apt-get install ffmpeg`

Mac: `brew install ffmpeg --with-libass --with-opus --with-fdk-aac`

### Windows

Assuming you have Python already installed..

- Download FFmpeg for windows from [here](http://ffmpeg.zeranoe.com/builds/). Copy `ffmpeg.exe` from bin folder (of FFmpeg) to Scripts folder (in your python's installation directory).

- Download the zip file of this repository and extract its contents in your python's installation folder.

- Change your current working directory to python's installation directory. Shift+right-click on empty area and open cmd and type:

`"Scripts/pip.exe" install -U -r requirements.txt`

- If you do not want to naviagte to your python folder from the command-line everytime you want to run the script, you can have your python 'PATH' environment variables set and then you can run the script from any directory.

## Instructions for Downloading Songs

- For all available options, run `python spotdl.py --help` (or for windows run `python.exe spotdl.py --help`).

```
usage: spotdl.py [-h] (-s SONG | -l LIST | -u USERNAME) [-n] [-m] [-f] [-v]
                 [-i INPUT_EXT] [-o OUTPUT_EXT]

Download and convert songs from Spotify, Youtube etc.

optional arguments:
  -h, --help            show this help message and exit
  -s SONG, --song SONG  download song by spotify link or name (default: None)
  -l LIST, --list LIST  download songs from a file (default: None)
  -u USERNAME, --username USERNAME
                        load user's playlists into <playlist_name>.txt
                        (default: None)
  -m, --manual          choose the song to download manually (default: False)
  -a, --avconv          Use avconv for conversion. If not set
                        defaults to FFmpeg (default: False)
  -v, --verbose         show debug output (default: False)
  -i INPUT_EXT, --input_ext INPUT_EXT
                        prefered input format .m4a or .webm (Opus) (default:
                        .m4a)
  -o OUTPUT_EXT, --output_ext OUTPUT_EXT
                        prefered output extension .mp3 or .m4a (AAC) (default:
                        .mp3)
```

#### Downloading by Name

For example

- We want to download Hello by Adele, simply run `python spotdl.py --song "adele hello"`.

- The script will automatically look for the best matching song and download it in the folder `Music/` placed in your current directory.

- It will now convert the song to an mp3 and try to fix meta-tags and album-art by looking up on Spotify.

#### Downloading by Spotify Link (Recommended)

For example

- We want to download the same song (i.e: Hello by Adele) but using Spotify Link this time that looks like  `http://open.spotify.com/track/1MDoll6jK4rrk2BcFRP5i7`, you can copy it from your Spotify desktop or mobile app by right clicking or long tap on the song and copy HTTP link.

- Run `python spotdl.py --song http://open.spotify.com/track/1MDoll6jK4rrk2BcFRP5i7`, it should download Hello by Adele.

- Just like before, it will again convert the song to an mp3 but since we used a Spotify HTTP link, the script is guaranteed to fetch the correct meta-tags and album-art.

#### Download multiple songs at once

For example

- We want to download `Hello by Adele`, `The Nights by Avicci` and `21 Guns by Green Day` just using a single command.

Let's suppose, we have the Spotify link for only `Hello by Adele` and `21 Guns by Green Day`.

No problem!

- Just make a `list.txt` in the same folder as the script and add all the songs you want to download, in our case it is

(if you are on windows, just edit `list.txt` - i.e `C:\Python27\list.txt`)

```
https://open.spotify.com/track/1MDoll6jK4rrk2BcFRP5i7
the nights avicci
http://open.spotify.com/track/64yrDBpcdwEdNY9loyEGbX
```

- Now pass `--list=list.txt` to the script, i.e `python spotdl.py --list=list.txt` and it will start downloading songs mentioned in `list.txt`.

- You can stop downloading songs by hitting `ctrl+c`, the script will automatically resume from the song where you stopped it the next time you want to download the songs present in `list.txt`.

- Songs that are already downloaded will be skipped and not be downloaded again.

#### Downloading playlists

- You can also load songs from any playlist provided you have spotify username of that user.

- Try running `python spotdl.py -u <your_username>`, it will show all your public playlists.

- Once you select the one you want to download, the script will load all the tracks from the playlist into `<playlist_name>.txt`

- Then you can simply run `python spotdl.py --list=<playlist_name>.txt` to download them all!

## FAQ

#### I get system cannot find the specified file when downloading?

Check out these issues [#22](https://github.com/Ritiek/Spotify-Downloader/issues/22), [#35](https://github.com/Ritiek/Spotify-Downloader/issues/35), [#36](https://github.com/Ritiek/Spotify-Downloader/issues/36).

#### How can I download whole playlist with its URI?

~~Currently this is not possible without generating unique tokens from Spotify but you can copy all the songs from a playlist and paste them in `list.txt`. I am avoiding tokens as much possible to retain the portability of this tool but if you would like to add it as an optional feature to this tool, PR's welcome!~~
This feature has been added!

#### You write horrible code. What's wrong with you?

I'm trying...

## Disclaimer

Downloading copyright songs may be illegal in your country. This tool is for educational purposes only and was created only to show how Spotify's API can be exploited to download music from YouTube. Please support the artists by buying their music.

## License

```The MIT License```
